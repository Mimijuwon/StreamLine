# 🤝 Contributing to StreamLine

Thank you for considering contributing to StreamLine! We're building something that will help millions of families stay connected across borders, and we'd love your help.

---

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Commit Guidelines](#commit-guidelines)
- [Pull Request Process](#pull-request-process)
- [Issue Labels](#issue-labels)
- [Community](#community)

---

## 📜 Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inspiring community for all. We expect everyone to:

✅ **Be respectful** - Treat everyone with respect and kindness  
✅ **Be inclusive** - Welcome diverse perspectives and backgrounds  
✅ **Be collaborative** - Work together toward common goals  
✅ **Be constructive** - Offer and accept constructive criticism gracefully  
✅ **Focus on impact** - Remember we're building to help real families  

❌ **Zero tolerance for:**
- Harassment, discrimination, or offensive behavior
- Trolling, insulting comments, or personal attacks
- Publishing others' private information
- Any conduct that would be inappropriate in a professional setting

**If you experience or witness unacceptable behavior, please report it to conduct@streamline.finance**

---

## 🎯 How Can I Contribute?

### For Developers

#### 🦀 Rust/Soroban Developers
- Build smart contracts for escrow, savings pools, multi-sig
- Optimize gas costs and contract efficiency
- Write comprehensive tests for contract security
- **Issues**: Look for `soroban`, `smart-contract`, `rust`

#### 📱 Mobile/Frontend Developers
- Build React Native mobile app
- Create Progressive Web App (PWA)
- Design responsive, accessible UI components
- Implement offline-first capabilities
- **Issues**: Look for `frontend`, `mobile`, `react-native`, `ui-ux`

#### ⚙️ Backend Developers
- Build REST/GraphQL APIs
- Integrate Stellar Horizon API
- Implement transaction monitoring
- Set up background job processing
- **Issues**: Look for `backend`, `api`, `node.js`, `database`

#### ⛓️ Blockchain/Web3 Developers
- Integrate Stellar SDK
- Work with Anchors for fiat on/off-ramps
- Implement multi-sig wallets
- Optimize path payments
- **Issues**: Look for `stellar`, `blockchain`, `web3`

### For Non-Developers

#### 🎨 Designers
- Create UI/UX designs for mobile and web
- Design app icons, logos, marketing materials
- Conduct user research and usability testing
- **Issues**: Look for `design`, `ui-ux`, `user-research`

#### 🌍 Translators
- Translate app interface and documentation
- Localize for specific markets (Philippines, Venezuela, India, etc.)
- Review translations for cultural appropriateness
- **Issues**: Look for `translation`, `localization`, `i18n`

#### 📝 Technical Writers
- Write documentation and tutorials
- Create API documentation
- Improve README and contribution guides
- Write blog posts about features
- **Issues**: Look for `documentation`, `content`, `tutorial`

#### 📊 Data Analysts
- Analyze transaction patterns
- Create dashboards for insights
- Help with fraud detection algorithms
- **Issues**: Look for `analytics`, `data`, `metrics`

#### 🧪 QA Testers
- Test new features on various devices
- Report bugs with detailed reproduction steps
- Perform security testing
- **Issues**: Look for `testing`, `qa`, `bug`

---

## 🚀 Getting Started

### 1. Find an Issue

Browse our [issue tracker](https://github.com/YOUR-USERNAME/streamline/issues) and look for:

- **`good-first-issue`** - Perfect if you're new to the project
- **`help-wanted`** - We need help on these
- **`beginner-friendly`** - Great learning opportunities
- **Your expertise area** - Filter by `frontend`, `backend`, `soroban`, etc.

**Not sure where to start?** Comment on issues asking for guidance - we're here to help!

### 2. Claim an Issue

Comment on the issue saying "I'd like to work on this!" and:
- Ask any clarifying questions
- Share your proposed approach (for complex issues)
- Mention estimated timeline

A maintainer will assign it to you and provide guidance.

### 3. Set Up Your Environment

Follow the [Quick Start guide](README.md#quick-start-for-contributors) in the README.

**Need help?** Join our [Discord](https://discord.gg/streamline) and ask in `#dev-help`

---

## 🔄 Development Workflow

### 1. Fork & Clone

```bash
# Fork the repo on GitHub, then:
git clone https://github.com/YOUR-USERNAME/streamline.git
cd streamline
git remote add upstream https://github.com/ORIGINAL-OWNER/streamline.git
```

### 2. Create a Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

**Branch naming:**
- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation updates
- `refactor/` - Code refactoring
- `test/` - Test additions/fixes

### 3. Make Changes

- Write clean, documented code
- Follow our [coding standards](#coding-standards)
- Add tests for new functionality
- Update documentation as needed

### 4. Test Your Changes

```bash
# Run all tests
npm test

# Run specific test suite
npm test -- transaction.test.js

# Test smart contracts
cd contracts && cargo test

# Lint your code
npm run lint
```

### 5. Commit Your Changes

Follow our [commit guidelines](#commit-guidelines):

```bash
git add .
git commit -m "feat: add SMS notification for transaction confirmation"
```

### 6. Push & Create PR

```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub!

---

## 💻 Coding Standards

### General Principles

✅ **Write clean, readable code** - Others will maintain it  
✅ **Comment complex logic** - Explain the "why", not the "what"  
✅ **Keep functions small** - Single responsibility principle  
✅ **Handle errors gracefully** - Always assume things can fail  
✅ **Write tests** - Aim for 80%+ coverage on new code  

### JavaScript/TypeScript

```javascript
// ✅ Good
async function sendRemittance(senderId, recipientId, amount) {
  // Validate inputs
  if (!amount || amount <= 0) {
    throw new Error('Amount must be positive');
  }
  
  try {
    const transaction = await stellar.sendPayment({
      from: senderId,
      to: recipientId,
      amount: amount
    });
    
    return transaction;
  } catch (error) {
    logger.error('Failed to send remittance', { error, senderId, recipientId });
    throw error;
  }
}

// ❌ Bad
function send(s, r, a) {
  return stellar.sendPayment({ from: s, to: r, amount: a });
}
```

**Standards:**
- Use async/await over callbacks
- Use const/let, never var
- Use meaningful variable names
- 2-space indentation
- ESLint compliant

### Rust/Soroban

```rust
// ✅ Good
#[contract]
pub struct EscrowContract;

#[contractimpl]
impl EscrowContract {
    /// Creates a new escrow with specified conditions
    /// 
    /// # Arguments
    /// * `env` - Contract environment
    /// * `sender` - Address initiating escrow
    /// * `recipient` - Address receiving funds
    /// * `amount` - Amount to escrow
    pub fn create_escrow(
        env: Env,
        sender: Address,
        recipient: Address,
        amount: i128,
    ) -> Result<EscrowId, EscrowError> {
        // Implementation
    }
}

// ❌ Bad
pub fn create(e: Env, s: Address, r: Address, a: i128) -> EscrowId {
    // No docs, unclear parameters
}
```

**Standards:**
- Document all public functions
- Use Result types for error handling
- Write comprehensive tests
- Follow Rust naming conventions

### Database Queries

```javascript
// ✅ Good - Parameterized queries
const user = await db.query(
  'SELECT * FROM users WHERE id = $1',
  [userId]
);

// ❌ Bad - SQL injection risk
const user = await db.query(
  `SELECT * FROM users WHERE id = ${userId}`
);
```

---

## 📝 Commit Guidelines

We follow [Conventional Commits](https://www.conventionalcommits.org/) for clear, semantic commit history.

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- **feat**: New feature
- **fix**: Bug fix
- **docs**: Documentation changes
- **style**: Code style/formatting (no logic change)
- **refactor**: Code refactoring
- **test**: Adding/updating tests
- **chore**: Maintenance tasks, dependencies

### Examples

```bash
feat(wallet): add multi-signature wallet support

Implements multi-sig wallets allowing 2-of-3 approval for transactions
over $1000. Includes Soroban contract and UI components.

Closes #123

---

fix(sms): resolve Twilio API rate limiting

Implements exponential backoff and queuing for SMS notifications
to handle rate limits gracefully.

Fixes #456

---

docs(api): add OpenAPI documentation for transaction endpoints

Closes #789
```

### Best Practices

✅ **Use imperative mood** - "add feature" not "added feature"  
✅ **First line < 72 characters** - Keep it concise  
✅ **Reference issues** - Use "Closes #123" or "Fixes #456"  
✅ **Explain why** - In body, explain motivation for changes  

---

## 🔀 Pull Request Process

### Before Submitting

- [ ] Code follows our style guidelines
- [ ] All tests pass locally
- [ ] Added tests for new functionality
- [ ] Updated relevant documentation
- [ ] Commit messages follow guidelines
- [ ] No merge conflicts with main branch

### PR Template

When creating a PR, include:

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
How did you test this?

## Screenshots (if applicable)
Add screenshots for UI changes

## Checklist
- [ ] Tests pass
- [ ] Documentation updated
- [ ] No breaking changes (or documented)

## Related Issues
Closes #123
```

### Review Process

1. **Automated checks** - CI/CD must pass (tests, linting, build)
2. **Code review** - At least 1 maintainer approval required
3. **Testing** - Reviewer tests functionality
4. **Merge** - Maintainer merges when approved

**Typical timeline:** 2-5 days for review

### Getting Feedback

- Be patient - reviewers are volunteers
- Respond to feedback constructively
- Ask questions if feedback is unclear
- Make requested changes promptly

---

## 🏷️ Issue Labels

### Priority
- `P0-critical` - Security issues, app-breaking bugs
- `P1-high` - Important features, significant bugs
- `P2-medium` - Normal priority
- `P3-low` - Nice-to-have improvements

### Difficulty
- `good-first-issue` - Perfect for newcomers
- `beginner-friendly` - Learning opportunity
- `intermediate` - Some project knowledge needed
- `advanced` - Requires deep expertise

### Type
- `bug` - Something isn't working
- `feature` - New functionality
- `enhancement` - Improve existing feature
- `documentation` - Docs need improvement

### Area
- `frontend` - UI/UX, web app
- `backend` - API, server, database
- `soroban` - Smart contracts
- `mobile` - React Native app
- `devops` - Infrastructure, CI/CD

### Status
- `help-wanted` - We need contributors
- `in-progress` - Someone is working on this
- `blocked` - Waiting on dependency
- `wontfix` - Not planned to fix

---

## 👥 Community

### Communication Channels

- **Discord** - [Join here](https://discord.gg/streamline)
  - `#general` - General discussion
  - `#dev-help` - Ask for development help
  - `#feature-ideas` - Discuss new features
  - `#showcase` - Share your work

- **GitHub Discussions** - Long-form technical discussions
- **Twitter** - [@StreamLineApp](https://twitter.com/StreamLineApp)
- **Monthly Community Calls** - First Tuesday of each month

### Getting Help

**Stuck on something?**

1. Check [documentation](README.md) and [wiki](https://github.com/YOUR-USERNAME/streamline/wiki)
2. Search existing [issues](https://github.com/YOUR-USERNAME/streamline/issues)
3. Ask in Discord `#dev-help`
4. Create a new issue with `question` label

**We're here to help - no question is too basic!**

### Recognition

We value all contributions! Contributors get:

- 💰 **Drips funding** - Earn based on contributions
- ⭐ **Listed in README** - Public recognition
- 🎓 **Learning opportunities** - Mentorship from experienced devs
- 🌟 **Portfolio project** - Build something that matters
- 🤝 **Community** - Connect with developers worldwide

---

## 🎉 First Time Contributors

**Never contributed to open source before?** We're excited to have you!

### Your First Contribution

1. **Browse `good-first-issue` label**
2. **Comment "I'd like to try this!"**
3. **Ask for guidance** - We'll help you through it
4. **Submit your PR** - No matter how small!

### Learning Resources

- [How to Contribute to Open Source](https://opensource.guide/how-to-contribute/)
- [First Contributions](https://github.com/firstcontributions/first-contributions)
- [Git Basics](https://git-scm.com/book/en/v2)
- [Our Wiki](https://github.com/YOUR-USERNAME/streamline/wiki)

**Every expert was once a beginner. We all start somewhere!**

---

## 🙏 Thank You!

Every contribution, no matter how small, makes a difference. You're helping:

- Families stay connected across borders
- Workers keep more of their hard-earned money
- Communities thrive despite distance

**Together, we're building something beautiful. Welcome to StreamLine! 💙**

---

<div align="center">

**Questions?** Join our [Discord](https://discord.gg/streamline) or open an [issue](https://github.com/YOUR-USERNAME/streamline/issues)

*Made with 💙 by contributors like you*

</div>
