# Cloudflare Pages Deployment Guide

## Repository Information
- **Repository**: rookie-sports/rookie-website
- **Branch**: main
- **Type**: Static HTML website (no build process required)

## Deployment Options

This repository is configured with **two deployment methods**. Choose the one that best fits your workflow:

### 🚀 Option 1: Automatic GitHub Actions Deployment (Recommended)
**Best for**: Automated deployments on every push, CI/CD integration

The repository includes a pre-configured GitHub Actions workflow that automatically deploys to Cloudflare Pages whenever you push to the `main` branch.

**Setup Steps**:
1. Follow the instructions in `SETUP_SECRETS.md` to configure GitHub secrets
2. Push a commit to the `main` branch (or manually trigger the workflow)
3. The site will automatically deploy to Cloudflare Pages
4. Check the "Actions" tab to see deployment status

**Advantages**:
- ✅ Fully automated - deploy on every push
- ✅ Preview deployments for pull requests
- ✅ Deployment status visible in GitHub
- ✅ No manual intervention needed after setup

### 🖱️ Option 2: Cloudflare Dashboard Connection
**Best for**: One-time setup, prefer UI over automation

Connect your GitHub repository directly through the Cloudflare dashboard.

**Setup Steps**: See "Manual Dashboard Setup" section below.

**Advantages**:
- ✅ No GitHub secrets required
- ✅ Easy visual setup
- ✅ Still provides automatic deployments on push
- ✅ Managed entirely through Cloudflare UI

---

## Manual Dashboard Setup Instructions

### Step 1: Access Cloudflare Dashboard
1. Log in to your Cloudflare account at https://dash.cloudflare.com/
2. Navigate to "Workers & Pages" from the left sidebar
3. Click "Create application" → "Pages" → "Connect to Git"

### Step 2: Connect GitHub Repository
1. Click "Connect GitHub" (authorize Cloudflare if this is your first time)
2. Select the organization: **rookie-sports**
3. Select the repository: **rookie-website**
4. Click "Begin setup"

### Step 3: Configure Build Settings
Use the following configuration:

- **Project name**: `rookie-website`
- **Production branch**: `main`
- **Framework preset**: None (or "Static HTML")
- **Build command**: (leave empty - no build needed)
- **Build output directory**: `.` or `/`
- **Root directory**: (leave as default `/`)

### Step 4: Environment Variables
No environment variables are required for this static site.

### Step 5: Deploy
1. Click "Save and Deploy"
2. Wait for the initial deployment to complete (usually 1-2 minutes)
3. Your site will be available at: `https://rookie-website.pages.dev`
   - If that name is taken, Cloudflare will assign: `https://rookie-website-xxx.pages.dev`

### Step 6: Verify Automatic Deployments
Once connected, Cloudflare Pages will automatically:
- ✅ Deploy on every push to the `main` branch
- ✅ Create preview deployments for pull requests
- ✅ Provide deployment status in GitHub commit checks
- ✅ Show deployment history in Cloudflare dashboard

---

## GitHub Actions Workflow Details

The repository includes `.github/workflows/cloudflare-pages.yml` which:
- Triggers on push to `main` branch
- Triggers on pull requests to `main` branch (creates preview deployments)
- Uses the official Cloudflare Pages action
- Requires two secrets: `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID`

**Configuration**:
```yaml
projectName: rookie-website
directory: .
```

To use this workflow, follow the setup instructions in `SETUP_SECRETS.md`.

---

## Expected Deployment URL

After deployment, your site will be accessible at one of these URLs:

- **Primary**: `https://rookie-website.pages.dev`
- **Alternative** (if name is taken): `https://rookie-website-xxx.pages.dev`

The exact URL will be displayed:
1. In the Cloudflare dashboard after first deployment
2. In GitHub Actions workflow output (if using GitHub Actions)
3. In the Cloudflare Pages deployment logs

**Update this section after deployment with your actual URL:**
- **Production URL**: `_______________` (fill in after first deployment)

---

## Free Tier Details

Cloudflare Pages Free Tier includes:
- ✅ Unlimited sites
- ✅ Unlimited requests
- ✅ Unlimited bandwidth
- ✅ 500 builds per month
- ✅ 1 concurrent build
- ✅ Automatic HTTPS
- ✅ Global CDN
- **Cost**: $0/month

---

## Post-Deployment Checklist

- [ ] Verify the deployment URL is accessible
- [ ] Test that the site displays correctly (ROOKIE logo, tagline, contact email)
- [ ] Test automatic deployment by pushing a small change to main
- [ ] Verify preview deployments work by creating a pull request
- [ ] Document the final deployment URL in this file
- [ ] (Optional) Configure custom domain if needed
- [ ] (Optional) Set up Cloudflare Web Analytics

---

## Custom Domain Setup (Optional)

To use a custom domain like `www.rookie.sports`:

1. Go to your Cloudflare Pages project
2. Click "Custom domains" tab
3. Click "Set up a custom domain"
4. Enter your domain name
5. Follow the DNS configuration instructions
6. Wait for DNS propagation (usually a few minutes)

**Note**: Your domain must be managed by Cloudflare for this to work seamlessly.

---

## Troubleshooting

### Deployment fails
- Verify the repository contains valid HTML files (`index.html` exists)
- Check that the build output directory is set to `.` or `/`
- Ensure the `main` branch is selected as the production branch

### Site shows 404 error
- Confirm `index.html` is in the root directory of the repository
- Check the build output directory setting
- Review deployment logs in Cloudflare dashboard

### GitHub Actions workflow fails
- Verify both secrets are set correctly (see `SETUP_SECRETS.md`)
- Check that the API token has "Cloudflare Pages - Edit" permission
- Ensure the Account ID is correct

### Changes not appearing
- Check that you pushed to the `main` branch
- Wait 1-2 minutes for deployment to complete
- Clear browser cache or try incognito mode
- Check deployment status in Cloudflare dashboard or GitHub Actions

---

## Alternative: Using Wrangler CLI

If you prefer CLI-based deployment:

```bash
# Install wrangler globally
npm install -g wrangler

# Login to Cloudflare
wrangler login

# Deploy the site
cd /path/to/rookie-website
wrangler pages deploy . --project-name=rookie-website --branch=main

# View deployment
wrangler pages deployment list --project-name=rookie-website
```

---

## Repository Structure

```
rookie-website/
├── .github/
│   └── workflows/
│       └── cloudflare-pages.yml    # GitHub Actions workflow
├── .cloudflare-pages-config.json   # Cloudflare Pages configuration
├── index.html                       # Main HTML file
├── style.css                        # Stylesheet
├── CLOUDFLARE_DEPLOYMENT.md         # This file
├── SETUP_SECRETS.md                 # GitHub secrets setup guide
└── README.md                        # Project overview
```

---

## Support

- **Cloudflare Pages Documentation**: https://developers.cloudflare.com/pages/
- **GitHub Actions Documentation**: https://docs.github.com/en/actions
- **Cloudflare Community**: https://community.cloudflare.com/

---

## Notes

- This is a static HTML site with no build process required
- The site consists of `index.html` and `style.css`
- No frameworks, dependencies, or package managers needed
- Deployment is instant - no compilation or bundling
- The site uses a minimal, brutalist design with Times New Roman typography
