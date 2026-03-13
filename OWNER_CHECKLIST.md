# 🚀 Cloudflare Pages Deployment - Owner Checklist

This is your step-by-step guide to deploying the rookie-website to Cloudflare Pages.

**Estimated Time**: 10-15 minutes  
**Cost**: $0 (Cloudflare Pages free tier)  
**Prerequisites**: Cloudflare account, GitHub repository access

---

## Choose Your Deployment Method

You have two options. Pick the one that works best for you:

- **Option A**: GitHub Actions (automated, requires setting up secrets) → Go to Section A
- **Option B**: Cloudflare Dashboard (manual setup, no secrets needed) → Go to Section B

---

## 📋 SECTION A: GitHub Actions Deployment (Recommended)

### Step 1: Get Your Cloudflare API Token

1. [ ] Log in to Cloudflare: https://dash.cloudflare.com/
2. [ ] Click your profile icon (top right) → "My Profile"
3. [ ] Click "API Tokens" in the left sidebar
4. [ ] Click "Create Token" button
5. [ ] Click "Create Custom Token"
6. [ ] Configure the token:
   - **Token name**: `GitHub Actions - Rookie Website`
   - **Permissions**: 
     - Account → Cloudflare Pages → Edit
   - **Account Resources**: 
     - Include → Select your account
7. [ ] Click "Continue to summary"
8. [ ] Click "Create Token"
9. [ ] **IMPORTANT**: Copy the token and save it somewhere safe (you'll only see it once!)
   - Token format: `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`

### Step 2: Get Your Cloudflare Account ID

1. [ ] Still in Cloudflare Dashboard, click "Workers & Pages" in the left sidebar
2. [ ] Look at the right sidebar - you'll see "Account ID" under "Account details"
3. [ ] Copy the Account ID
   - Format: `a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6` (32 characters)
   - Alternative: Look at the URL - it's the string after `dash.cloudflare.com/`

### Step 3: Add Secrets to GitHub

1. [ ] Go to: https://github.com/rookie-sports/rookie-website
2. [ ] Click the "Settings" tab (top navigation)
3. [ ] In the left sidebar, click "Secrets and variables" → "Actions"
4. [ ] Click "New repository secret"
5. [ ] Add first secret:
   - **Name**: `CLOUDFLARE_API_TOKEN` (exactly as shown)
   - **Secret**: Paste the API token from Step 1
   - Click "Add secret"
6. [ ] Click "New repository secret" again
7. [ ] Add second secret:
   - **Name**: `CLOUDFLARE_ACCOUNT_ID` (exactly as shown)
   - **Secret**: Paste the Account ID from Step 2
   - Click "Add secret"
8. [ ] Verify both secrets are listed (you should see two green entries)

### Step 4: Trigger First Deployment

**Option 4A - Automatic (make a small change)**:
1. [ ] Edit any file in the repository (e.g., add a space to README.md)
2. [ ] Commit and push to the `main` branch
3. [ ] Go to the "Actions" tab in GitHub
4. [ ] Watch the "Deploy to Cloudflare Pages" workflow run

**Option 4B - Manual trigger**:
1. [ ] Go to the "Actions" tab in GitHub
2. [ ] Click "Deploy to Cloudflare Pages" in the left sidebar
3. [ ] Click "Run workflow" button (right side)
4. [ ] Select "Branch: main"
5. [ ] Click "Run workflow"

### Step 5: Verify Deployment

1. [ ] Wait for the workflow to complete (1-2 minutes)
2. [ ] Click on the completed workflow run
3. [ ] Click on the "Deploy to Cloudflare Pages" job
4. [ ] Expand the "Deploy to Cloudflare Pages" step
5. [ ] Look for the deployment URL in the output
   - Should be: `https://rookie-website.pages.dev` or similar
6. [ ] Copy the URL and open it in your browser
7. [ ] Verify the site displays correctly:
   - [ ] ROOKIE logo appears
   - [ ] Tagline: "AI-powered basketball training and shot analytics"
   - [ ] Contact email: info@rookie.sports

### Step 6: Document the URL

1. [ ] Open `CLOUDFLARE_DEPLOYMENT.md` in the repository
2. [ ] Find the "Production URL" line near the middle of the file
3. [ ] Replace `_______________` with your actual deployment URL
4. [ ] Commit and push the change

### ✅ Section A Complete!

Your site is now live and will automatically deploy whenever you push to the `main` branch.

---

## 📋 SECTION B: Cloudflare Dashboard Deployment

### Step 1: Access Cloudflare Pages

1. [ ] Log in to Cloudflare: https://dash.cloudflare.com/
2. [ ] Click "Workers & Pages" in the left sidebar
3. [ ] Click "Create application" button
4. [ ] Click "Pages" tab
5. [ ] Click "Connect to Git"

### Step 2: Connect GitHub Repository

1. [ ] Click "Connect GitHub"
2. [ ] If prompted, authorize Cloudflare to access your GitHub account
3. [ ] Select "Only select repositories"
4. [ ] Choose "rookie-sports/rookie-website" from the dropdown
5. [ ] Click "Install & Authorize"
6. [ ] You should see the repository listed
7. [ ] Click "Begin setup" next to "rookie-website"

### Step 3: Configure Build Settings

1. [ ] **Project name**: Enter `rookie-website`
2. [ ] **Production branch**: Select `main`
3. [ ] **Framework preset**: Select "None" or leave as default
4. [ ] **Build command**: Leave empty (no build needed)
5. [ ] **Build output directory**: Enter `.` (just a period)
6. [ ] **Root directory**: Leave as `/` (default)
7. [ ] **Environment variables**: Leave empty (none needed)

### Step 4: Deploy

1. [ ] Review all settings one more time
2. [ ] Click "Save and Deploy" button
3. [ ] Wait for deployment to complete (1-2 minutes)
4. [ ] You'll see a success message with your deployment URL

### Step 5: Verify Deployment

1. [ ] Copy the deployment URL shown on screen
   - Should be: `https://rookie-website.pages.dev` or `https://rookie-website-xxx.pages.dev`
2. [ ] Open the URL in your browser
3. [ ] Verify the site displays correctly:
   - [ ] ROOKIE logo appears
   - [ ] Tagline: "AI-powered basketball training and shot analytics"
   - [ ] Contact email: info@rookie.sports

### Step 6: Document the URL

1. [ ] Open `CLOUDFLARE_DEPLOYMENT.md` in the repository
2. [ ] Find the "Production URL" line near the middle of the file
3. [ ] Replace `_______________` with your actual deployment URL
4. [ ] Commit and push the change

### Step 7: Verify Automatic Deployments

1. [ ] Make a small change to the repository (e.g., edit README.md)
2. [ ] Commit and push to the `main` branch
3. [ ] Go back to Cloudflare dashboard → Workers & Pages → rookie-website
4. [ ] You should see a new deployment starting automatically
5. [ ] Wait for it to complete
6. [ ] Refresh your site URL to see the changes

### ✅ Section B Complete!

Your site is now live and will automatically deploy whenever you push to the `main` branch.

---

## 🎯 Post-Deployment Tasks (Both Options)

### Verify Everything Works

1. [ ] Site is accessible at the deployment URL
2. [ ] All content displays correctly
3. [ ] CSS styling is applied
4. [ ] Contact email link works
5. [ ] Site loads quickly (should be instant via Cloudflare CDN)

### Test Automatic Deployments

1. [ ] Make a small change (e.g., update tagline in index.html)
2. [ ] Commit and push to `main`
3. [ ] Wait 1-2 minutes
4. [ ] Refresh the site and verify changes appear

### Optional Enhancements

- [ ] Set up custom domain (if you own rookie.sports)
- [ ] Enable Cloudflare Web Analytics
- [ ] Configure preview deployments for pull requests
- [ ] Add more content to the site

---

## 📊 Deployment Status

**Deployment URL**: _______________  
**Deployment Date**: _______________  
**Deployment Method**: [ ] GitHub Actions  [ ] Cloudflare Dashboard  
**Status**: [ ] Live  [ ] Pending  [ ] Issues  

---

## 🆘 Troubleshooting

### GitHub Actions fails with "Authentication error"
- **Solution**: Double-check that `CLOUDFLARE_API_TOKEN` secret is set correctly
- Verify the API token has "Cloudflare Pages - Edit" permission
- Try creating a new API token

### GitHub Actions fails with "Account not found"
- **Solution**: Verify `CLOUDFLARE_ACCOUNT_ID` is correct
- Check that you copied the full Account ID (32 characters)

### Site shows 404 error
- **Solution**: Verify `index.html` is in the root directory
- Check build output directory is set to `.` or `/`
- Review deployment logs for errors

### Changes not appearing on the site
- **Solution**: Wait 1-2 minutes for deployment to complete
- Clear browser cache (Ctrl+Shift+R or Cmd+Shift+R)
- Check deployment status in Cloudflare dashboard or GitHub Actions

### Dashboard setup: Can't find the repository
- **Solution**: Make sure you authorized Cloudflare to access the repository
- Go to GitHub → Settings → Applications → Cloudflare Pages
- Grant access to rookie-sports/rookie-website

---

## 📚 Additional Resources

- **Cloudflare Pages Docs**: https://developers.cloudflare.com/pages/
- **GitHub Actions Docs**: https://docs.github.com/en/actions
- **Repository**: https://github.com/rookie-sports/rookie-website
- **Detailed Guide**: See `CLOUDFLARE_DEPLOYMENT.md` in the repository
- **Secrets Setup**: See `SETUP_SECRETS.md` in the repository

---

## ✅ Final Checklist

- [ ] Deployment method chosen (GitHub Actions or Dashboard)
- [ ] Secrets configured (if using GitHub Actions)
- [ ] First deployment completed successfully
- [ ] Site is accessible at deployment URL
- [ ] Deployment URL documented in CLOUDFLARE_DEPLOYMENT.md
- [ ] Automatic deployments tested and working
- [ ] All content displays correctly

**Congratulations! Your site is live! 🎉**

---

**Questions or Issues?**  
Review the troubleshooting section above or check the detailed guides:
- `CLOUDFLARE_DEPLOYMENT.md` - Full deployment documentation
- `SETUP_SECRETS.md` - GitHub secrets setup (for GitHub Actions method)
