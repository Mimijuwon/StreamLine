# 🌟 StreamLine

### *Send home. Instantly. For pennies.*

[![Stellar](https://img.shields.io/badge/Built%20on-Stellar-blue)](https://stellar.org)
[![Drips Wave](https://img.shields.io/badge/Funded%20by-Drips%20Wave-brightgreen)](https://drips.network/wave)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Contributors Welcome](https://img.shields.io/badge/contributors-welcome-orange.svg)](CONTRIBUTING.md)

---

## 🌍 The Problem

**700+ million people** send money across borders to support their families. Traditional remittance services charge:
- **6-12% in fees** on every transaction
- **$15-30 minimum fees** making small transfers impossible
- **2-5 days** for money to arrive
- **Poor exchange rates** that hide additional costs

**For a $50 transfer, fees can consume $10-15. That's rent money. That's food money. That's a child's education.**

---

## ✨ Our Solution

**StreamLine** is a Stellar-based remittance platform that enables **instant, near-zero-cost cross-border payments** designed for:

- 🏃‍♀️ **Gig workers** sending money home weekly
- 👨‍💻 **Remote workers** in emerging markets
- 👨‍⚕️ **Healthcare workers** supporting families abroad
- 🌏 **Diaspora communities** staying connected

### Why StreamLine?

✅ **Under $0.01 per transaction** - Powered by Stellar's efficiency  
✅ **Instant settlement** - Money arrives in seconds, not days  
✅ **Mobile-first** - Works on basic smartphones  
✅ **SMS support** - Recipients don't need crypto knowledge  
✅ **Local currency** - Automatic conversion at fair rates  
✅ **Agent network** - Cash out locally without a bank account  

---

## 🚀 How It Works

```
┌─────────────┐         ┌──────────────┐         ┌─────────────┐
│   Sender    │────────>│  StreamLine  │────────>│  Recipient  │
│  (Mobile)   │  $50    │   (Stellar)  │  $49.99 │   (SMS)     │
└─────────────┘         └──────────────┘         └─────────────┘
     USA                 Instant + $0.01              Philippines
                         Settlement
```

1. **Sender** enters recipient's phone number and amount
2. **StreamLine** converts to stablecoins on Stellar
3. **Stellar network** settles in 3-5 seconds
4. **Recipient** gets SMS notification to cash out at local agent or mobile wallet
5. **Agent** provides local currency instantly

---

## 🛠️ Tech Stack

### Blockchain Layer
- **Stellar Blockchain** - Fast, low-cost transactions
- **Soroban Smart Contracts** - Escrow, auto-conversion, savings pools
- **Stellar Anchors** - Fiat on/off-ramps
- **USDC/EURC** - Stable value transfer

### Application Layer
- **Frontend**: React Native (iOS/Android), Progressive Web App
- **Backend**: Node.js, Express, Rust (Soroban contracts)
- **Database**: PostgreSQL, Redis (caching)
- **APIs**: Stellar SDK, Horizon, Anchor integrations
- **Notifications**: Twilio (SMS), Firebase (push)

### Infrastructure
- **Hosting**: AWS/Railway
- **CI/CD**: GitHub Actions
- **Monitoring**: Sentry, DataDog
- **Security**: KYC/AML compliance, multi-sig wallets

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────┐
│                     Client Layer                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │ Mobile App   │  │  Web App     │  │  SMS Gateway │  │
│  │ (React Nat.) │  │   (PWA)      │  │   (Twilio)   │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
                           ▼
┌─────────────────────────────────────────────────────────┐
│                    API Gateway                           │
│              (Node.js + Express + Auth)                  │
└─────────────────────────────────────────────────────────┘
                           ▼
┌─────────────────────────────────────────────────────────┐
│                  Business Logic Layer                    │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │  Transaction │  │   Wallet     │  │   Agent      │  │
│  │   Service    │  │   Manager    │  │   Network    │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
                           ▼
┌─────────────────────────────────────────────────────────┐
│                  Stellar Integration                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │   Horizon    │  │   Soroban    │  │   Anchors    │  │
│  │     API      │  │  Contracts   │  │  (Fiat I/O)  │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
                           ▼
                 ⭐ Stellar Network ⭐
```

---

## 🎯 Project Roadmap

### Phase 1: MVP (Months 1-2) 🚧 Current Phase
- [ ] Stellar wallet creation and management
- [ ] Basic send/receive P2P transfers
- [ ] SMS notification system
- [ ] Single currency pair (USD → PHP)
- [ ] Simple web interface
- [ ] Transaction history

### Phase 2: Core Features (Months 3-4)
- [ ] Soroban smart contracts for escrow
- [ ] Multi-currency support (5+ corridors)
- [ ] Mobile app (React Native)
- [ ] QR code payments
- [ ] Recurring payment scheduling
- [ ] Exchange rate optimization

### Phase 3: Agent Network (Months 5-6)
- [ ] Agent onboarding system
- [ ] Cash-out locations map
- [ ] Agent reputation/rating
- [ ] Commission management
- [ ] Regional liquidity pools
- [ ] KYC/AML compliance lite

### Phase 4: Advanced Features (Months 7-9)
- [ ] Micro-savings pools
- [ ] Group remittance splitting
- [ ] Loyalty rewards in XLM
- [ ] Analytics dashboard
- [ ] White-label solution for NGOs
- [ ] Offline transaction queuing

### Phase 5: Scale & Optimize (Months 10+)
- [ ] Multi-chain support
- [ ] AI-powered fraud detection
- [ ] B2B partnerships
- [ ] Regional regulatory compliance
- [ ] 10+ currency corridors
- [ ] Native blockchain wallet integration

---

## 🚀 Quick Start for Contributors

### Prerequisites
```bash
- Node.js 18+
- Rust 1.70+ (for Soroban)
- Stellar CLI
- PostgreSQL 14+
- Git
```

### Setup Development Environment

1. **Clone the repository**
```bash
git clone https://github.com/YOUR-USERNAME/streamline.git
cd streamline
```

2. **Install dependencies**
```bash
# Backend
cd backend
npm install

# Frontend
cd ../frontend
npm install

# Smart contracts
cd ../contracts
cargo build --target wasm32-unknown-unknown --release
```

3. **Configure environment**
```bash
cp .env.example .env
# Edit .env with your Stellar testnet credentials
```

4. **Setup database**
```bash
cd backend
npm run db:migrate
npm run db:seed
```

5. **Start development servers**
```bash
# Terminal 1 - Backend
cd backend
npm run dev

# Terminal 2 - Frontend
cd frontend
npm run dev

# Terminal 3 - Soroban local network (optional)
stellar network start local
```

6. **Access the application**
```
Frontend: http://localhost:3000
Backend API: http://localhost:5000
API Docs: http://localhost:5000/api-docs
```

### Run Tests
```bash
# Backend tests
cd backend
npm test

# Frontend tests
cd frontend
npm test

# Smart contract tests
cd contracts
cargo test
```

---

## 🎓 Learning Resources

New to Stellar or blockchain development? Start here:

- 📘 [Stellar Documentation](https://developers.stellar.org/)
- 🦀 [Soroban Smart Contracts](https://soroban.stellar.org/)
- 📱 [React Native Guide](https://reactnative.dev/docs/getting-started)
- 🎓 [Our Wiki](https://github.com/YOUR-USERNAME/streamline/wiki) - In-depth tutorials

---

## 🤝 Contributing

We love contributors! Whether you're a:
- 🦀 **Rust developer** → Soroban smart contracts
- 📱 **Mobile developer** → React Native app
- ⛓️ **Blockchain enthusiast** → Stellar integration
- 🎨 **Designer** → UI/UX improvements
- 🌍 **Translator** → Localization
- 📊 **Data analyst** → Transaction analytics
- 📝 **Writer** → Documentation

**There's a place for you here!**

Check out our [Contributing Guide](CONTRIBUTING.md) and look for issues tagged:
- `good-first-issue` - Perfect for newcomers
- `help-wanted` - We need your expertise
- `beginner-friendly` - Learning opportunity
- `high-impact` - Critical features

---

## 💰 Funding & Support

StreamLine is proudly supported by:
- 🌊 **Drips Network Wave** - Open source funding
- ⭐ **Stellar Community Fund** - Grant recipient
- 🏗️ **Your contributions** - Drips splits for active contributors

### How Funding Works
Contributors earn through Drips dependency trees based on their contributions. The more you contribute, the more you earn!

---

## 📊 Current Stats

- **Contributors**: Join us as a founding contributor!
- **Commits**: Growing daily
- **Issues**: 30+ tagged and ready
- **Stars**: Give us a ⭐ if you believe in the mission

---

## 🌟 Why This Matters

Every transaction on StreamLine means:
- A child staying in school instead of dropping out
- A family having enough food for the month
- Medical bills getting paid on time
- Dreams staying alive across borders

**We're not just building an app. We're building financial bridges that connect families.**

---

## 📜 License

MIT License - See [LICENSE](LICENSE) for details

---

## 🔗 Links

- **Website**: [streamline.finance](https://streamline.finance) *(coming soon)*
- **Documentation**: [docs.streamline.finance](https://docs.streamline.finance) *(coming soon)*
- **Drips Profile**: [drips.network/app/projects/YOUR-ID](https://drips.network)
- **Twitter**: [@StreamLineApp](https://twitter.com/StreamLineApp) *(coming soon)*
- **Discord**: [Join our community](https://discord.gg/streamline) *(coming soon)*

---

## 🙏 Acknowledgments

Built with ❤️ by developers worldwide who believe in:
- Financial inclusion
- Open source collaboration
- The power of blockchain for good

Special thanks to:
- **Stellar Development Foundation** for the incredible blockchain
- **Drips Network** for funding open source
- **Our contributors** - You make this possible

---

<div align="center">

### 💙 Join us in making remittances fair for everyone

**[Start Contributing](CONTRIBUTING.md)** • **[View Issues](https://github.com/YOUR-USERNAME/streamline/issues)** • **[Join Discord](https://discord.gg/streamline)**

*Made with 💙 by the StreamLine community*

</div>
