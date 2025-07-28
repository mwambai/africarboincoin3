# Netlify Deployment Guide for Africarboncoin

## 🚀 Quick Deployment Steps

### 1. Connect Repository to Netlify

1. **Sign up/Login to Netlify**
   - Go to [netlify.com](https://netlify.com)
   - Sign in with your GitHub account

2. **Create New Site**
   - Click "New site from Git"
   - Choose your Africarboncoin repository
   - Select the main branch

### 2. Build Settings

Configure these settings in Netlify:

```
Base directory: .
Build command: npm run build
Publish directory: dist/public
Node version: 20
```

### 3. Environment Variables

Add these in **Site settings → Environment variables**:

#### Essential Variables
```
DATABASE_URL=postgresql://neondb_owner:npg_psBajbN4Wth0@ep-frosty-grass-a6wa7flv.us-west-2.aws.neon.tech/neondb?sslmode=require
SESSION_SECRET=141b536c9771aa53b583c5682a60f1ce35ec9c07029e20bc625f38639ff00bf5
NODE_ENV=production
```

#### Optional Payment Variables
```
STRIPE_SECRET_KEY=your-stripe-secret-key
VITE_STRIPE_PUBLIC_KEY=your-stripe-public-key
PAYPAL_CLIENT_ID=your-paypal-client-id
PAYPAL_CLIENT_SECRET=your-paypal-client-secret
```

#### Optional Email Variables
```
SENDGRID_API_KEY=your-sendgrid-api-key
ZOHO_MAIL_USERNAME=your-email@domain.com
ZOHO_MAIL_PASSWORD=your-app-password
```

## 📁 Project Configuration

Your project includes `netlify.toml` with optimized settings:

- **Build Configuration**: Automated build process
- **Function Handling**: API routes as Netlify Functions
- **Client-side Routing**: SPA routing support
- **Security Headers**: Production-ready security
- **Asset Caching**: Optimized static asset delivery

## 🔧 Manual Deployment (Alternative)

If you prefer manual deployment:

### Option 1: Netlify CLI
```bash
# Install Netlify CLI
npm install -g netlify-cli

# Login to Netlify
netlify login

# Deploy to production
netlify deploy --prod --dir=dist/public
```

### Option 2: Drag & Drop
1. Run `npm run build` locally
2. Go to Netlify dashboard
3. Drag the `dist/public` folder to deploy

## 🌐 Domain Configuration

### Custom Domain
1. Go to **Site settings → Domain management**
2. Click "Add custom domain"
3. Configure DNS settings as instructed
4. SSL certificate is automatically provisioned

### Netlify Subdomain
- Your site will be available at `https://your-site-name.netlify.app`
- You can customize the subdomain in site settings

## 🔍 Monitoring & Analytics

### Build Logs
- View deployment logs in **Deploys** tab
- Monitor build status and errors
- Access function logs for API debugging

### Performance
- Lighthouse scores available in dashboard
- Core Web Vitals monitoring
- Asset optimization suggestions

## 🐛 Troubleshooting

### Common Issues

**Build Failures**
```bash
# Check build logs for specific errors
# Ensure all dependencies are in package.json
# Verify Node.js version compatibility
```

**API Function Errors**
```bash
# Check function logs in Netlify dashboard
# Verify environment variables are set
# Ensure database connectivity
```

**Client-side Routing Issues**
```bash
# Verify netlify.toml redirect rules
# Check that SPA routing is configured
# Ensure index.html is in publish directory
```

### Database Connection
- Verify DATABASE_URL is correctly set
- Ensure Neon database accepts external connections
- Check connection string format

### Environment Variables
- Variables must be set in Netlify dashboard
- Restart deployment after adding new variables
- Verify sensitive values don't have extra quotes

## 🚀 Performance Optimization

### Build Performance
- Build time: ~40-60 seconds on Netlify
- Consider build plugins for optimization
- Use build cache for faster rebuilds

### Runtime Performance
- Global CDN for fast content delivery
- Automatic asset optimization
- Edge function support for dynamic content

### Bundle Size
- Current bundle: ~2.2MB (compressed to ~759KB)
- Consider code splitting for better performance
- Use dynamic imports where possible

## 🔐 Security Features

### Automatic HTTPS
- SSL certificates automatically provisioned
- HTTP to HTTPS redirects enabled
- Certificate renewal handled automatically

### Security Headers
- Content Security Policy headers
- XSS protection enabled
- Clickjacking protection
- MIME type sniffing prevention

### Environment Security
- Environment variables encrypted at rest
- Build-time variable injection
- No sensitive data in client bundle

## 📊 Analytics & Monitoring

### Built-in Analytics
- Traffic and performance metrics
- User behavior insights
- Form submission tracking
- A/B testing capabilities

### External Integration
- Google Analytics support
- Custom tracking implementation
- Performance monitoring tools
- Error tracking services

## 🔄 Continuous Deployment

### Automatic Deployments
- Deploy on every push to main branch
- Preview deployments for pull requests
- Branch-specific deployment rules
- Deploy hooks for external triggers

### Deploy Previews
- Test changes before going live
- Share preview links with team
- A/B testing capabilities
- Rollback to previous deployments

## 💡 Pro Tips

1. **Branch Deploys**: Set up branch-specific deployments for staging
2. **Build Hooks**: Use webhooks for triggering builds from external services
3. **Split Testing**: Use Netlify's built-in A/B testing features
4. **Edge Functions**: Consider edge functions for dynamic functionality
5. **Analytics**: Enable Netlify Analytics for detailed insights

## 📞 Support

- **Netlify Documentation**: [docs.netlify.com](https://docs.netlify.com)
- **Community Support**: [answers.netlify.com](https://answers.netlify.com)
- **Status Page**: [netlifystatus.com](https://netlifystatus.com)

Your Africarboncoin platform is now ready for production deployment on Netlify!

## 🎯 Next Steps After Deployment

1. **Test all functionality** on the live site
2. **Configure custom domain** if needed
3. **Set up monitoring and alerts**
4. **Enable analytics** for usage insights
5. **Configure backup and recovery** procedures

Your carbon credit marketplace will be live and accessible worldwide with Netlify's global CDN!