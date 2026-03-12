# Cloudflare Pages Deployment Guide

## Repository Information
- **Repository**: rookie-sports/rookie-website
- **Branch**: main
- **Type**: Static HTML website

## Cloudflare Pages Setup Instructions

### Step 1: Access Cloudflare Dashboard
1. Log in to your Cloudflare account at https://dash.cloudflare.com/
2. Navigate to "Workers & Pages" from the left sidebar
3. Click "Create application" → "Pages" → "Connect to Git"

### Step 2: Connect GitHub Repository
1. Click "Connect GitHub" (authorize if first time)
2. Select the organization: **rookie-sports**
3. Select the repository: **rookie-website**
4. Click "Begin setup"

### Step 3: Configure Build Settings
Use the following configuration:

- **Project name**: `rookie-website` (or your preferred name)
- **Production branch**: `main`
- **Build command**: (leave empty - no build needed)
- **Build output directory**: `/` or `.`
- **Root directory**: `/` (leave as default)

### Step 4: Environment Variables
No environment variables are required for this static site.

### Step 5: Deploy
1. Click "Save and Deploy"
2. Wait for the initial deployment to complete (usually 1-2 minutes)
3. Your site will be available at: `https://rookie-website-xxx.pages.dev`
   (where xxx is a unique identifier assigned by Cloudflare)

## Automatic Deployment Configuration

Once connected, Cloudflare Pages will automatically:
- Deploy on every push to the `main` branch
- Create preview deployments for pull requests
- Provide deployment status in GitHub

## Free Tier Details
- ✅ Unlimited sites
- ✅ Unlimited requests
- ✅ Unlimited bandwidth
- ✅ 500 builds per month
- ✅ 1 concurrent build
- **Cost**: $0/month

## Post-Deployment Checklist
- [ ] Verify the deployment URL is accessible
- [ ] Test automatic deployment by pushing a change to main
- [ ] Document the final deployment URL
- [ ] (Optional) Configure custom domain if needed

## Deployment URL
After deployment, update this section with the actual URL:
- **Production URL**: `https://rookie-website-xxx.pages.dev`

## Troubleshooting
- If deployment fails, check that the repository contains valid HTML files
- Ensure the output directory is set to `/` or `.`
- Verify that the main branch is selected as the production branch

## Alternative: Using Wrangler CLI

If you prefer CLI-based deployment:

```bash
# Install wrangler (if not already installed)
npm install -g wrangler

# Login to Cloudflare
wrangler login

# Deploy the site
cd /path/to/rookie-website
wrangler pages deploy . --project-name=rookie-website --branch=main

# Set up automatic deployments via GitHub Actions (optional)
# Create .github/workflows/deploy.yml with Cloudflare Pages action
```

## Notes
- This is a static HTML site with no build process required
- The site consists of index.html and style.css
- No frameworks or dependencies to install
