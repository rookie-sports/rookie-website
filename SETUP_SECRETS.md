# GitHub Secrets Setup for Cloudflare Pages

To enable automatic deployments via GitHub Actions, you need to configure the following secrets in your GitHub repository.

## Required Secrets

### 1. CLOUDFLARE_API_TOKEN
- **Purpose**: Authenticates GitHub Actions to deploy to Cloudflare Pages
- **How to obtain**:
  1. Log in to Cloudflare Dashboard: https://dash.cloudflare.com/
  2. Go to "My Profile" → "API Tokens"
  3. Click "Create Token"
  4. Use the "Edit Cloudflare Workers" template OR create a custom token with:
     - Permissions: `Account - Cloudflare Pages - Edit`
  5. Copy the token (you'll only see it once!)

### 2. CLOUDFLARE_ACCOUNT_ID
- **Purpose**: Identifies your Cloudflare account
- **How to obtain**:
  1. Log in to Cloudflare Dashboard
  2. Go to "Workers & Pages"
  3. Your Account ID is displayed on the right sidebar
  4. Or find it in the URL: `https://dash.cloudflare.com/<ACCOUNT_ID>/...`

## Adding Secrets to GitHub

1. Go to your repository: https://github.com/rookie-sports/rookie-website
2. Click "Settings" → "Secrets and variables" → "Actions"
3. Click "New repository secret"
4. Add each secret:
   - Name: `CLOUDFLARE_API_TOKEN`, Value: (paste your API token)
   - Name: `CLOUDFLARE_ACCOUNT_ID`, Value: (paste your account ID)

## Verification

After adding the secrets:
1. Push a commit to the `main` branch
2. Go to the "Actions" tab in your repository
3. You should see the "Deploy to Cloudflare Pages" workflow running
4. Once complete, your site will be live!

## Alternative: Dashboard-Only Setup (No GitHub Actions)

If you prefer not to use GitHub Actions, you can connect your repository directly through the Cloudflare dashboard:
1. Follow the instructions in `CLOUDFLARE_DEPLOYMENT.md`
2. Cloudflare will handle deployments automatically without needing GitHub secrets
3. You can delete the `.github/workflows/cloudflare-pages.yml` file if not needed
