# GitHub Secrets Setup for Cloudflare Pages

To enable automatic deployments via GitHub Actions, you need to configure the following secrets in your GitHub repository.

## Required Secrets

### 1. CLOUDFLARE_API_TOKEN
- **Purpose**: Authenticates GitHub Actions to deploy to Cloudflare Pages
- **How to obtain**:
  1. Log in to Cloudflare Dashboard: https://dash.cloudflare.com/
  2. Click on your profile icon (top right) → "My Profile" → "API Tokens"
  3. Click "Create Token"
  4. **Option A - Use Template (Recommended)**:
     - Look for "Create Custom Token" section
     - Set the following permissions:
       - **Account** → **Cloudflare Pages** → **Edit**
     - Click "Continue to summary"
     - Click "Create Token"
  5. **Option B - Manual Configuration**:
     - Click "Create Custom Token"
     - Token name: "GitHub Actions - Rookie Website"
     - Permissions:
       - Account → Cloudflare Pages → Edit
     - Account Resources: Include → Select your account
     - Click "Continue to summary" → "Create Token"
  6. **IMPORTANT**: Copy the token immediately (you'll only see it once!)
  7. Store it securely - you'll add it to GitHub in the next step

### 2. CLOUDFLARE_ACCOUNT_ID
- **Purpose**: Identifies your Cloudflare account
- **How to obtain**:
  1. Log in to Cloudflare Dashboard: https://dash.cloudflare.com/
  2. Click on "Workers & Pages" in the left sidebar
  3. Your Account ID is displayed in the right sidebar under "Account details"
  4. Alternatively, look at the URL when viewing Workers & Pages:
     - URL format: `https://dash.cloudflare.com/<ACCOUNT_ID>/workers-and-pages`
     - The Account ID is the string of letters/numbers after the domain
  5. Copy the Account ID (it looks like: `a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6`)

## Adding Secrets to GitHub

1. Go to your repository: https://github.com/rookie-sports/rookie-website
2. Click "Settings" tab (top navigation)
3. In the left sidebar, click "Secrets and variables" → "Actions"
4. Click "New repository secret" button
5. Add the first secret:
   - **Name**: `CLOUDFLARE_API_TOKEN`
   - **Secret**: Paste the API token you created above
   - Click "Add secret"
6. Click "New repository secret" again
7. Add the second secret:
   - **Name**: `CLOUDFLARE_ACCOUNT_ID`
   - **Secret**: Paste your Account ID
   - Click "Add secret"

## Verification

After adding both secrets:

1. Go to the "Actions" tab in your repository
2. You should see the "Deploy to Cloudflare Pages" workflow
3. To trigger a deployment:
   - **Option A**: Make a small change to the repository and push to main
   - **Option B**: Go to Actions → "Deploy to Cloudflare Pages" → "Run workflow" → "Run workflow"
4. Watch the workflow run - it should complete successfully in 1-2 minutes
5. The workflow output will show your deployment URL
6. Visit the URL to verify your site is live!

## Troubleshooting

### Workflow fails with "Authentication error"
- Double-check that CLOUDFLARE_API_TOKEN is set correctly
- Verify the API token has "Cloudflare Pages - Edit" permission
- Make sure the token hasn't expired

### Workflow fails with "Account not found"
- Verify CLOUDFLARE_ACCOUNT_ID is correct
- Check that the Account ID matches your Cloudflare account

### Workflow fails with "Project not found"
- This is normal on first deployment
- The workflow will automatically create the "rookie-website" project
- If it persists, create the project manually in Cloudflare dashboard first

## Alternative: Dashboard-Only Setup (No GitHub Actions)

If you prefer not to use GitHub Actions, you can connect your repository directly through the Cloudflare dashboard:
1. Follow the instructions in `CLOUDFLARE_DEPLOYMENT.md`
2. Cloudflare will handle deployments automatically without needing GitHub secrets
3. You can skip this entire secrets setup process

## Security Notes

- ✅ GitHub secrets are encrypted and only exposed to workflow runs
- ✅ Secret values are never displayed in logs
- ✅ API tokens can be revoked at any time from Cloudflare dashboard
- ⚠️ Never commit API tokens directly to your repository
- ⚠️ Limit API token permissions to only what's needed (Cloudflare Pages - Edit)
