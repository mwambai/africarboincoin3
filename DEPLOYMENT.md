# Africarboncoin Platform Deployment Guide

## Overview
This guide covers deploying the Africarboncoin platform across multiple cloud providers and containerized environments.

## Prerequisites
- Node.js 18+ runtime
- PostgreSQL database (Neon, Supabase, or managed PostgreSQL)
- Environment variables configured
- Domain name (optional but recommended)

## Environment Variables
Configure these essential environment variables for production:

```bash
# Core Application
NODE_ENV=production
PORT=5000
DATABASE_URL=postgresql://username:password@host:port/database

# Authentication
SESSION_SECRET=your-secure-session-secret
REPL_ID=your-repl-id (for Replit Auth)

# Payment Processing
STRIPE_SECRET_KEY=sk_live_...
VITE_STRIPE_PUBLIC_KEY=pk_live_...
PAYPAL_CLIENT_ID=your-paypal-client-id
PAYPAL_CLIENT_SECRET=your-paypal-client-secret

# Email Services
SENDGRID_API_KEY=SG.your-sendgrid-key
ZOHO_MAIL_USERNAME=your-email@domain.com
ZOHO_MAIL_PASSWORD=your-app-password
ZOHO_MAIL_HOST=smtp.zoho.com
ZOHO_MAIL_PORT=587

# Optional Features
OPENAI_API_KEY=sk-...
TWILIO_ACCOUNT_SID=AC...
TWILIO_AUTH_TOKEN=...
```

## Deployment Options

### 1. Vercel (Recommended for Serverless)

**Setup:**
1. Connect your GitHub repository to Vercel
2. Configure environment variables in the Vercel dashboard
3. The included `vercel.json` handles build configuration automatically

**Configuration:**
The project includes a properly configured `vercel.json`:
```json
{
  "version": 2,
  "builds": [
    {
      "src": "dist/index.js",
      "use": "@vercel/node"
    },
    {
      "src": "dist/public/**",
      "use": "@vercel/static"
    }
  ],
  "routes": [
    {
      "src": "/api/(.*)",
      "dest": "/dist/index.js"
    },
    {
      "src": "/(.*)",
      "dest": "/dist/public/$1"
    }
  ]
}
```

**Commands:**
```bash
# Build and deploy
vercel --prod

# Local preview
vercel dev
```

**Features:**
- Automatic HTTPS
- Global CDN
- Serverless functions
- Preview deployments

### 2. Railway (Database Included)

**Setup:**
1. Connect GitHub repository
2. Railway automatically provisions PostgreSQL
3. Environment variables auto-configured

**Commands:**
```bash
# Deploy via CLI
railway login
railway link
railway up
```

**Features:**
- Managed PostgreSQL database
- Automatic deployments
- Built-in monitoring
- Custom domains

### 3. Render (Full-Stack Hosting)

**Setup:**
1. Create web service from GitHub
2. Add PostgreSQL database service
3. Configure environment variables

**Configuration:**
- Build Command: `npm run build`
- Start Command: `npm run start`
- Environment: Node.js 18

**Features:**
- Managed databases
- Automatic SSL certificates
- Health checks
- Auto-scaling

### 4. Netlify (JAMstack Approach)

**Setup:**
1. Deploy frontend to Netlify
2. Use Netlify Functions for API
3. External database required

**Build Settings:**
- Build command: `npm run build`
- Publish directory: `dist/public`

### 5. Docker Deployment

**Quick Start:**
```bash
# Build image
docker build -t africarboncoin .

# Run container
docker run -p 5000:5000 --env-file .env africarboncoin

# Use Docker Compose
docker-compose up -d
```

**Features:**
- Consistent environments
- Easy scaling
- Container orchestration
- Multi-service setup

### 6. Self-Hosted (VPS/Dedicated Server)

**Ubuntu/Debian Setup:**
```bash
# Install Node.js 18
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Install PM2 for process management
npm install -g pm2

# Clone and setup project
git clone <repository-url>
cd africarboncoin
npm install
npm run build

# Start with PM2
pm2 start dist/server.js --name "africarboncoin"
pm2 startup
pm2 save
```

**Nginx Configuration:**
```nginx
server {
    listen 80;
    server_name your-domain.com;

    location /api {
        proxy_pass http://localhost:5000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }

    location / {
        root /path/to/africarboncoin/dist/public;
        try_files $uri $uri/ /index.html;
    }
}
```

## Database Setup

### Neon (Serverless PostgreSQL)
```bash
# Connection string format
DATABASE_URL=postgresql://username:password@ep-cool-darkness-123456.us-east-1.aws.neon.tech/neondb?sslmode=require
```

### Supabase
```bash
# Connection string from Supabase dashboard
DATABASE_URL=postgresql://postgres:password@db.project.supabase.co:5432/postgres
```

### Self-Managed PostgreSQL
```bash
# Install PostgreSQL
sudo apt-get install postgresql postgresql-contrib

# Create database and user
sudo -u postgres createdb africarboncoin
sudo -u postgres createuser --interactive
```

## SSL/HTTPS Setup

### Let's Encrypt (Free SSL)
```bash
# Install Certbot
sudo apt install certbot python3-certbot-nginx

# Generate certificate
sudo certbot --nginx -d your-domain.com

# Auto-renewal
sudo systemctl enable certbot.timer
```

### Cloudflare (Recommended)
1. Add domain to Cloudflare
2. Update nameservers
3. Enable SSL/TLS encryption
4. Configure security rules

## Monitoring & Logging

### Health Checks
- Endpoint: `GET /api/health`
- Returns server status and uptime
- Use for load balancer health checks

### Logging Setup
```bash
# PM2 logs
pm2 logs africarboncoin

# Custom log directory
mkdir -p /var/log/africarboncoin
```

### Monitoring Tools
- **Uptime Robot**: Free uptime monitoring
- **New Relic**: Application performance monitoring
- **Sentry**: Error tracking and reporting

## Performance Optimization

### Caching
- Enable Redis for session storage
- Implement CDN for static assets
- Use database query caching

### Scaling
- Horizontal scaling with load balancers
- Database read replicas
- Container orchestration (Kubernetes)

## Security Checklist

- [ ] HTTPS enabled with valid SSL certificate
- [ ] Environment variables secured
- [ ] Database connections encrypted
- [ ] Rate limiting implemented
- [ ] CORS properly configured
- [ ] Security headers set
- [ ] Regular dependency updates
- [ ] Backup strategy in place

## Troubleshooting

### Common Issues

**Build Failures:**
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

**Database Connection Issues:**
```bash
# Test database connection
node -e "require('./dist/server/db.js')"
```

**Port Conflicts:**
```bash
# Change port in production
export PORT=8080
```

### Log Analysis
```bash
# Check application logs
tail -f /var/log/africarboncoin/app.log

# Database query logs
tail -f /var/log/postgresql/postgresql.log
```

## Deployment Checklist

- [ ] Environment variables configured
- [ ] Database migrations applied
- [ ] SSL certificate installed
- [ ] Health checks passing
- [ ] Monitoring enabled
- [ ] Backup system configured
- [ ] Domain DNS configured
- [ ] Performance testing completed
- [ ] Security audit passed
- [ ] Documentation updated

## Support

For deployment issues:
1. Check the health endpoint: `/api/health`
2. Review application logs
3. Verify environment variables
4. Test database connectivity
5. Contact support with error details

## Cost Estimates

### Vercel
- **Hobby**: Free for personal projects
- **Pro**: $20/month per user
- **Enterprise**: Custom pricing

### Railway
- **Starter**: $5/month
- **Developer**: $20/month
- **Team**: $99/month

### Render
- **Free**: Limited resources
- **Starter**: $7/month
- **Standard**: $25/month

### Self-Hosted (VPS)
- **Basic**: $5-10/month (DigitalOcean, Linode)
- **Production**: $20-50/month
- **Enterprise**: $100+/month

Choose the deployment option that best fits your budget, scale requirements, and technical expertise.