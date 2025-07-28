# Africarboncoin Platform

A comprehensive carbon credit marketplace platform that combines blockchain technology with real-world carbon sequestration projects across Africa. The platform features Africoin (AFC), a carbon-backed cryptocurrency with mining and staking capabilities, alongside a carbon credit marketplace with real-time wallet functionality.

## 🌍 Overview

Africarboncoin is designed to create sustainable economic opportunities across Africa by leveraging:
- **Blockchain Technology**: Secure, transparent carbon credit transactions
- **AI-Powered Analytics**: Drone data analysis for carbon offset verification
- **Real-time Trading**: Live marketplace for carbon credits
- **Multi-Currency Support**: African currencies (MAD, ZAR, TND) plus global currencies
- **Hardware Wallet Integration**: Ledger device support for secure transactions

## 🚀 Features

### Core Platform
- **Carbon Credit Trading**: Buy, sell, and manage carbon credits
- **Africoin (AFC)**: Carbon-backed cryptocurrency with staking rewards
- **Real-time Wallet**: MetaMask integration with live balance tracking
- **Multi-Currency Support**: African and international currency conversion
- **Project Registry**: Carbon sequestration projects with location data

### Advanced Capabilities
- **AI Analysis**: Drone data processing for carbon verification
- **Hardware Wallets**: Ledger integration for secure transactions
- **Payment Processing**: Stripe and PayPal integration
- **Email Notifications**: Automated transaction and verification emails
- **Admin Dashboard**: User management and credit allocation tools

## 🛠 Tech Stack

### Frontend
- **React 18** with TypeScript
- **Vite** for fast development and building
- **Tailwind CSS** + **shadcn/ui** for modern UI components
- **TanStack Query** for state management
- **Wouter** for lightweight routing
- **Framer Motion** for animations

### Backend
- **Node.js** with **Express.js**
- **TypeScript** with ES modules
- **Drizzle ORM** with PostgreSQL
- **WebSocket** support for real-time updates
- **Passport.js** for authentication

### Blockchain Integration
- **MetaMask** wallet connectivity
- **Ledger** hardware wallet support
- **Ethereum** network compatibility
- Real-time transaction monitoring

### Database & Infrastructure
- **PostgreSQL** (Neon serverless)
- **Session Management** with PostgreSQL storage
- **Email Services** (Nodemailer + SendGrid)
- **Payment Processing** (Stripe + PayPal)

## 📦 Installation

### Prerequisites
- Node.js 18 or higher
- PostgreSQL database
- Git

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/africarboncoin.git
   cd africarboncoin
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment setup**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration values
   ```

4. **Database setup**
   ```bash
   npm run db:push
   ```

5. **Start development server**
   ```bash
   npm run dev
   ```

The application will be available at `http://localhost:5000`

## 🌐 Deployment

The platform supports multiple deployment options:

### Cloud Platforms
- **Vercel**: One-click serverless deployment
- **Railway**: Full-stack hosting with managed database
- **Render**: Auto-scaling web services with SSL
- **Netlify**: JAMstack deployment

### Containerized Deployment
```bash
# Docker
docker build -t africarboncoin .
docker run -p 5000:5000 africarboncoin

# Docker Compose
docker-compose up -d
```

### Automated Deployment
```bash
# Deploy to production
./scripts/deploy.sh production vercel

# Health check
./scripts/health-check.sh https://your-domain.com
```

## 🔧 Configuration

### Environment Variables

Copy `.env.example` to `.env` and configure:

```bash
# Application
NODE_ENV=development
DATABASE_URL=postgresql://...

# Authentication
SESSION_SECRET=your-secure-secret

# Payment Processing
STRIPE_SECRET_KEY=sk_...
PAYPAL_CLIENT_ID=...

# Email Services
SENDGRID_API_KEY=SG...
```

### Database Schema

The platform uses Drizzle ORM with PostgreSQL. Key tables include:
- `users` - User accounts and profiles
- `wallets` - Cryptocurrency wallets
- `transactions` - Transaction history
- `carbon_projects` - Carbon sequestration projects
- `orders` - Trading orders
- `drone_data` - AI analysis data

## 🔐 Security Features

- **Session Management**: PostgreSQL-backed sessions
- **Password Hashing**: bcrypt for secure password storage
- **Hardware Wallet Support**: Ledger integration
- **HTTPS**: SSL/TLS encryption
- **Rate Limiting**: API endpoint protection
- **Input Validation**: Zod schema validation

## 🧪 Testing

```bash
# Type checking
npm run check

# Health check
curl http://localhost:5000/api/health

# Build verification
npm run build
```

## 📊 API Endpoints

### Core APIs
- `GET /api/health` - Server health check
- `GET /api/wallet/balance` - Wallet balance
- `GET /api/wallet/transactions` - Transaction history
- `POST /api/wallet/send` - Send funds
- `GET /api/market/data` - Market data
- `GET /api/market/orders` - Trading orders

### Authentication
- `GET /api/auth/me` - Current user
- `GET /api/login` - Login endpoint
- `GET /api/logout` - Logout endpoint

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🌟 Features Roadmap

- [ ] Smart contract deployment for true decentralization
- [ ] Multi-chain support (Polygon, Avalanche, BSC)
- [ ] DeFi integrations (yield farming, staking pools)
- [ ] Mobile app development
- [ ] Carbon offset verification system
- [ ] Governance token implementation

## 📞 Support

For questions and support:
- Create an issue in this repository
- Check the [deployment guide](DEPLOYMENT.md)
- Review the [health check endpoint](http://localhost:5000/api/health)

## 🌍 Impact

Africarboncoin aims to:
- **Support African Communities**: Create economic opportunities through carbon projects
- **Environmental Conservation**: Incentivize carbon sequestration and offset projects
- **Blockchain Innovation**: Demonstrate real-world blockchain applications
- **Financial Inclusion**: Provide accessible financial services across Africa

---

**Built with ❤️ for a sustainable future in Africa**