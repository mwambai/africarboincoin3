# Africarboncoin Platform

## Overview

Africarboncoin is a comprehensive carbon credit marketplace platform that combines blockchain technology with real-world carbon sequestration projects. The platform enables users to buy, sell, and manage carbon credits while supporting environmental conservation efforts across Africa. It features a React-based frontend with a Node.js/Express backend, PostgreSQL database, and integrates with various third-party services including Ledger hardware wallets, payment processors, and AI-powered carbon analysis tools.

## System Architecture

### Frontend Architecture
- **Framework**: React with TypeScript
- **Build Tool**: Vite with custom configuration
- **UI Framework**: Tailwind CSS with shadcn/ui components
- **State Management**: TanStack Query for server state, React Context for global state
- **Routing**: Wouter for client-side routing
- **Authentication**: Replit Auth integration with fallback to traditional auth

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database ORM**: Drizzle ORM with PostgreSQL
- **Session Management**: PostgreSQL-backed sessions with connect-pg-simple
- **Authentication**: Dual auth system (Replit Auth + traditional username/password)
- **Email Service**: Nodemailer with Zoho Mail configuration

### Database Design
- **Primary Database**: PostgreSQL (Neon serverless)
- **ORM**: Drizzle with schema-first approach
- **Schema Location**: `shared/schema.ts` for type sharing between frontend and backend
- **Migrations**: Handled via Drizzle Kit

## Key Components

### Authentication System
- **Replit Integration**: Primary authentication method using OpenID Connect
- **Traditional Auth**: Username/password with bcrypt hashing as fallback
- **Email Verification**: Token-based email verification system
- **Password Reset**: Secure token-based password reset functionality
- **Session Management**: PostgreSQL-backed sessions with configurable TTL

### Wallet Management
- **Multiple Wallet Types**: Support for software wallets and hardware wallets (Ledger)
- **Hardware Wallet Integration**: Ledger device connectivity via WebUSB
- **Transaction Signing**: Secure transaction signing with hardware wallet support
- **Balance Tracking**: Real-time balance updates and transaction history
- **Multi-Currency Support**: African currencies (MAD, ZAR, TND) plus global currencies

### Carbon Credit System
- **Project Registry**: Carbon sequestration projects with location data
- **AI-Powered Analysis**: Drone data analysis for carbon offset verification
- **Blockchain Integration**: Smart contract interactions for carbon credit tokenization
- **Verification System**: Multi-step verification including drone data and AI analysis

### Market Features
- **Order Book**: Buy/sell orders with real-time updates
- **Currency Conversion**: Multi-currency support with real-time exchange rates
- **Transaction History**: Comprehensive transaction tracking and reporting
- **Price Charts**: Historical price data visualization

### Administrative Features
- **User Management**: Admin dashboard for user administration
- **Credit Allocation**: Administrative tools for carbon credit distribution
- **System Monitoring**: Platform health and performance monitoring
- **Resource Management**: FAQ and help documentation management

## Data Flow

### User Registration & Authentication
1. User registers via Replit Auth or traditional form
2. Email verification token sent via Zoho Mail
3. Session created in PostgreSQL sessions table
4. User profile stored in users table with unique ID

### Carbon Credit Transaction
1. User initiates buy/sell order through market interface
2. Order stored in orders table with pending status
3. Transaction recorded in transactions table
4. Wallet balance updated in wallets table
5. Real-time updates sent to connected clients

### Hardware Wallet Integration
1. User connects Ledger device via WebUSB
2. Device addresses retrieved and displayed
3. Transaction prepared with gas estimates
4. User confirms transaction on hardware device
5. Signed transaction broadcast to blockchain

## External Dependencies

### Payment Processing
- **Stripe**: Credit card processing for fiat currency transactions
- **PayPal**: Alternative payment method integration

### Email Services
- **Zoho Mail**: Transactional email delivery
- **SendGrid**: Backup email service provider

### Blockchain & Crypto
- **Ledger**: Hardware wallet integration
- **Ethereum**: Blockchain network for token operations
- **Neon Database**: Serverless PostgreSQL hosting

### Development & Build
- **Replit**: Development environment and deployment platform
- **Vite**: Frontend build tool and development server
- **Drizzle Kit**: Database schema management and migrations

## Deployment Strategy

### Development Environment
- **Platform**: Replit with Node.js 20 runtime
- **Database**: PostgreSQL 16 module
- **Hot Reload**: Vite development server with HMR
- **Port Configuration**: Backend on 5000, mapped to external port 80

### Production Deployment
- **Multi-Platform Support**: Vercel, Railway, Render, Netlify, Docker, Self-hosted
- **Build Process**: Vite build for frontend, esbuild for backend
- **Start Command**: `npm run start` serving built assets
- **Static Assets**: Served from `dist/public` directory
- **Database**: Neon serverless PostgreSQL with connection pooling
- **Health Checks**: `/api/health` endpoint for monitoring
- **SSL/HTTPS**: Automatic with cloud providers, Let's Encrypt for self-hosted

### Environment Configuration
- **Session Secret**: Configurable via environment variables
- **Email Credentials**: Zoho Mail configuration with fallback values
- **Database URL**: Required environment variable for PostgreSQL connection
- **Base URL**: Configurable for email links and redirects
- **Deployment Scripts**: Automated deployment with `scripts/deploy.sh`
- **Health Monitoring**: `scripts/health-check.sh` for uptime verification

### Supported Platforms
- **Vercel**: Serverless deployment with automatic HTTPS and global CDN
- **Railway**: Full-stack hosting with managed PostgreSQL database
- **Render**: Web services with built-in SSL and auto-scaling
- **Netlify**: JAMstack deployment with serverless functions
- **Docker**: Containerized deployment with docker-compose setup
- **Self-hosted**: VPS/dedicated server with PM2 process management

## Changelog

- June 15, 2025: Completed realtime wallet system with MetaMask integration
  - Added live balance tracking and transaction monitoring
  - Implemented send/receive/allocation functionality
  - Created test wallet with $250,000 allocated funds
  - Successfully processed transfer of 1,000 CCC to external address
  - Added WebSocket support for real-time updates
- June 14, 2025: Initial setup

## User Preferences

Preferred communication style: Simple, everyday language.