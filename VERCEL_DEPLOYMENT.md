# Vercel Deployment Guide for Africarboncoin

## Environment Variables Required

Add these environment variables in your Vercel dashboard:

### Essential Variables
```
NODE_ENV=production
DATABASE_URL=your-neon-database-url
SESSION_SECRET=your-secure-session-secret-min-32-chars
```

### Payment Processing (Optional)
```
STRIPE_SECRET_KEY=sk_live_...
VITE_STRIPE_PUBLIC_KEY=pk_live_...
PAYPAL_CLIENT_ID=your-paypal-client-id
PAYPAL_CLIENT_SECRET=your-paypal-client-secret
```

### Email Services (Optional)
```
SENDGRID_API_KEY=SG.your-sendgrid-key
ZOHO_MAIL_USERNAME=your-email@domain.com
ZOHO_MAIL_PASSWORD=your-app-password
ZOHO_MAIL_HOST=smtp.zoho.com
ZOHO_MAIL_PORT=587
```

## Deployment Steps

### Via Vercel Dashboard

1. **Create Vercel Account**
   - Go to [vercel.com](https://vercel.com)
   - Sign up with GitHub

2. **Import Repository**
   - Click "New Project"
   - Import your GitHub repository
   - Configure settings:
     - Framework: Other
     - Build Command: `npm run build`
     - Output Directory: `dist/public`
     - Install Command: `npm ci`

3. **Add Environment Variables**
   - Go to Project Settings → Environment Variables
   - Add all variables listed above

4. **Deploy**
   - Click "Deploy"
   - Your app will be live at `https://your-project.vercel.app`

### Via Vercel CLI

1. **Install Vercel CLI**
   ```bash
   npm i -g vercel
   ```

2. **Login to Vercel**
   ```bash
   vercel login
   ```

3. **Deploy**
   ```bash
   vercel --prod
   ```

## Database Setup

### Neon Database (Recommended)

1. **Create Neon Account**
   - Go to [neon.tech](https://neon.tech)
   - Create a new project

2. **Get Connection String**
   - Copy the connection string
   - Add as `DATABASE_URL` in Vercel

3. **Initialize Database**
   ```bash
   npm run db:push
   ```

## Post-Deployment

### Custom Domain (Optional)
1. Go to Project Settings → Domains
2. Add your custom domain
3. Configure DNS as instructed

### SSL Certificate
- Automatically provided by Vercel
- No additional configuration needed

## Monitoring

### Health Check
- Your app includes a health endpoint: `/api/health`
- Use for monitoring and uptime checks

### Logs
- View deployment logs in Vercel dashboard
- Monitor runtime logs in the Functions tab

## Troubleshooting

### Build Errors
- Check build logs in Vercel dashboard
- Ensure all dependencies are in package.json
- Verify environment variables are set

### Database Connection
- Verify DATABASE_URL is correct
- Ensure database accepts connections from Vercel IPs
- Check Neon database is not suspended

### Environment Variables
- Verify all required variables are set
- Check variable names match exactly
- Sensitive values should not have quotes

## Performance Optimization

### Build Time
- Current build time: ~40 seconds
- Consider code splitting for faster builds

### Bundle Size
- Main bundle: ~2.2MB
- Consider dynamic imports for optimization

## Security

### Environment Variables
- Never commit .env files
- Use Vercel's environment variable encryption
- Rotate secrets regularly

### Database Security
- Use connection pooling
- Enable SSL connections
- Regular security updates

Your Africarboncoin platform is now ready for production deployment on Vercel!