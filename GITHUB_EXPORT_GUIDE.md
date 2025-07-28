# GitHub Export Guide for Africarboncoin Platform

This guide will help you export your Africarboncoin platform from Replit to GitHub and set up continuous deployment.

## 🚀 Quick Export Steps

### 1. Create GitHub Repository

1. Go to [GitHub.com](https://github.com) and sign in
2. Click "New Repository" or visit [github.com/new](https://github.com/new)
3. Repository settings:
   - **Name**: `africarboncoin` (or your preferred name)
   - **Description**: "A comprehensive carbon credit marketplace platform for Africa"
   - **Visibility**: Choose Public or Private
   - **Initialize**: Leave unchecked (we'll push existing code)

### 2. Export from Replit

**Option A: Direct GitHub Integration (Recommended)**
1. In Replit, click the version control icon (Git) in the left sidebar
2. Click "Create a Git repository"
3. Click "Connect to GitHub"
4. Select your GitHub account and the repository you created
5. Click "Connect"
6. All your code will be automatically synced

**Option B: Manual Git Setup**
1. Open the Replit Shell
2. Initialize Git and push to GitHub:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Africarboncoin Platform"

# Add GitHub remote (replace with your repository URL)
git remote add origin https://github.com/yourusername/africarboncoin.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### 3. Repository Setup

After pushing to GitHub, your repository will include:

```
📁 Your Repository Structure:
├── 📄 README.md                 # Comprehensive project documentation
├── 📄 LICENSE                   # MIT License
├── 📄 CONTRIBUTING.md           # Contribution guidelines
├── 📄 DEPLOYMENT.md             # Deployment instructions
├── 📄 .gitignore                # Git ignore rules
├── 📄 .env.example              # Environment variables template
├── 📁 .github/
│   ├── 📁 workflows/
│   │   └── 📄 deploy.yml        # GitHub Actions CI/CD
│   └── 📁 ISSUE_TEMPLATE/
│       ├── 📄 bug_report.md     # Bug report template
│       └── 📄 feature_request.md # Feature request template
├── 📁 client/                   # Frontend React application
├── 📁 server/                   # Backend Express application
├── 📁 shared/                   # Shared schemas and types
├── 📁 scripts/                  # Deployment and utility scripts
├── 📄 package.json              # Dependencies and scripts
├── 📄 vercel.json               # Vercel deployment config
├── 📄 Dockerfile                # Docker configuration
└── 📄 docker-compose.yml        # Docker Compose setup
```

## 🔧 Post-Export Configuration

### 1. Update Repository Settings

1. **Branch Protection** (Settings → Branches):
   - Add rule for `main` branch
   - Require pull request reviews
   - Require status checks (GitHub Actions)

2. **Repository Topics** (About section):
   - Add tags: `blockchain`, `carbon-credits`, `react`, `typescript`, `africa`

3. **Repository Description**:
   ```
   🌍 Comprehensive carbon credit marketplace platform combining blockchain technology with real-world carbon sequestration projects across Africa
   ```

### 2. Environment Secrets Setup

For automated deployments, add these secrets in **Settings → Secrets and variables → Actions**:

#### Deployment Secrets
- `VERCEL_TOKEN` - Vercel deployment token
- `VERCEL_ORG_ID` - Vercel organization ID
- `VERCEL_PROJECT_ID` - Vercel project ID
- `RAILWAY_TOKEN` - Railway deployment token

#### Application Secrets
- `DATABASE_URL` - PostgreSQL connection string
- `SESSION_SECRET` - Secure session secret
- `STRIPE_SECRET_KEY` - Stripe payment processing
- `SENDGRID_API_KEY` - Email service API key

### 3. Enable GitHub Actions

Your repository includes automated CI/CD in `.github/workflows/deploy.yml`:

- **Testing**: Runs on every push and pull request
- **Type Checking**: Ensures TypeScript compilation
- **Build Verification**: Tests the build process
- **Health Checks**: Verifies API endpoints
- **Deployment**: Automatic deployment to Vercel (main) and Railway (develop)

## 🌐 Deployment Options

### Vercel (Recommended)

1. **Connect Repository**:
   - Go to [vercel.com](https://vercel.com)
   - Import your GitHub repository
   - Vercel will auto-detect the configuration

2. **Environment Variables**:
   - Add all variables from `.env.example`
   - Configure production database URL

3. **Custom Domain** (Optional):
   - Add your domain in Vercel dashboard
   - Update DNS settings as instructed

### Railway

1. **Connect Repository**:
   - Go to [railway.app](https://railway.app)
   - Create new project from GitHub
   - Railway will provision PostgreSQL automatically

2. **Configuration**:
   - Environment variables are auto-configured
   - Custom domain available in pro plans

### Docker Deployment

```bash
# Clone your repository
git clone https://github.com/yourusername/africarboncoin.git
cd africarboncoin

# Build and run with Docker Compose
docker-compose up -d

# Or build manually
docker build -t africarboncoin .
docker run -p 5000:5000 --env-file .env africarboncoin
```

## 🔄 Development Workflow

### 1. Local Development

```bash
# Clone your repository
git clone https://github.com/yourusername/africarboncoin.git
cd africarboncoin

# Install dependencies
npm install

# Setup environment
cp .env.example .env
# Edit .env with your configuration

# Start development
npm run dev
```

### 2. Contributing Workflow

```bash
# Create feature branch
git checkout -b feature/new-feature

# Make changes and commit
git add .
git commit -m "feat: add new feature"

# Push branch
git push origin feature/new-feature

# Create pull request on GitHub
```

### 3. Deployment Workflow

- **Development**: Push to `develop` branch → Auto-deploy to Railway
- **Production**: Push to `main` branch → Auto-deploy to Vercel
- **Manual**: Use deployment scripts in `scripts/` directory

## 📊 Repository Features

### 1. Issue Templates
- **Bug Reports**: Structured bug reporting with environment details
- **Feature Requests**: Comprehensive feature proposal template

### 2. GitHub Actions
- **Continuous Integration**: Automated testing and building
- **Continuous Deployment**: Automatic deployment to cloud platforms
- **Security Scanning**: Dependency vulnerability checks

### 3. Documentation
- **README.md**: Complete project overview and setup instructions
- **CONTRIBUTING.md**: Guidelines for contributors
- **DEPLOYMENT.md**: Comprehensive deployment instructions

### 4. Development Tools
- **Scripts**: Automated deployment and health check scripts
- **Docker**: Containerization for consistent deployments
- **Environment**: Template and example configurations

## 🎯 Next Steps

After exporting to GitHub:

1. **Customize Repository**:
   - Update README with your specific details
   - Add your own screenshots and demos
   - Customize license if needed

2. **Set Up Monitoring**:
   - Enable GitHub Security Advisories
   - Set up Dependabot for dependency updates
   - Configure branch protection rules

3. **Community Features**:
   - Create project boards for task management
   - Set up discussions for community engagement
   - Add contributor guidelines

4. **Continuous Improvement**:
   - Monitor GitHub Actions for build status
   - Review and merge pull requests
   - Update documentation as features evolve

## 🔗 Useful Links

- **Repository**: `https://github.com/yourusername/africarboncoin`
- **Issues**: `https://github.com/yourusername/africarboncoin/issues`
- **Actions**: `https://github.com/yourusername/africarboncoin/actions`
- **Wiki**: `https://github.com/yourusername/africarboncoin/wiki`

## 🆘 Troubleshooting

### Common Issues

**Push Rejected**:
```bash
# If you get push rejected, try:
git pull origin main --rebase
git push origin main
```

**Large Files**:
```bash
# Remove large files from git history
git rm --cached large-file.zip
echo "large-file.zip" >> .gitignore
git commit -m "Remove large file"
```

**Environment Variables**:
- Never commit `.env` files
- Use `.env.example` for documentation
- Set production secrets in deployment platform

Your Africarboncoin platform is now ready for GitHub! The repository includes everything needed for development, deployment, and community collaboration.