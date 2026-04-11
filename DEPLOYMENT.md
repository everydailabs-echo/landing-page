# EverydAI Labs Landing Page — Deployment Guide

## Current Status
✅ Landing page built and committed locally to git

**Location:** `/home/everydai-labs/agent/landing-page/`  
**Git status:** Local repo initialized with initial commit ready

---

## Deployment to Cloudflare Pages

### Option A: GitHub + Cloudflare Pages (Recommended)
This is the fastest path to get the landing page live with auto-deployment on code updates.

1. **Create GitHub account** (if not already done):
   - Go to https://github.com/signup
   - Use email: contact@everydailabs.com
   - Verify email (goes to your Gmail via Cloudflare routing)
   - Note your GitHub username

2. **Create a new repository on GitHub:**
   - Name: `landing-page` (or `everydai-labs-landing`)
   - Description: "EverydAI Labs official landing page"
   - Public repository (recommended for Cloudflare Pages)
   - Do NOT initialize with README, .gitignore, or license

3. **Push the local repo to GitHub:**
   ```bash
   cd /home/everydai-labs/agent/landing-page
   git remote add origin https://github.com/YOUR_USERNAME/landing-page.git
   git branch -M main
   git push -u origin main
   ```

4. **Connect to Cloudflare Pages:**
   - Go to Cloudflare Dashboard → Pages
   - Click "Create a project"
   - Select "Connect to Git"
   - Authorize GitHub and select your `landing-page` repo
   - Build settings:
     - Framework: None
     - Build command: (leave blank)
     - Build output directory: (leave blank)
   - Environment variables: (none needed)
   - Click "Save and Deploy"

5. **Configure domain:**
   - After deployment, go to project settings → Domains
   - Add custom domain: `everydailabs.com`
   - Add CNAME record in Cloudflare DNS (or follow prompts)
   - Set as production domain

---

### Option B: Direct Wrangler Deployment
If you want to deploy directly without GitHub (faster but requires Cloudflare API token):

1. **Get Cloudflare API token:**
   - Go to Cloudflare Dashboard → Account → API Tokens
   - Copy Global API Key or create a scoped token
   - Store in `pass`: `pass insert cloudflare/api-token`

2. **Deploy:**
   ```bash
   cd /home/everydai-labs/agent/landing-page
   wrangler pages deploy . --project-name everydai-labs
   ```

3. **Configure domain in Cloudflare Dashboard after deployment**

---

## After Deployment

✅ **Stripe website validation will unblock automatically** once the landing page is live at everydailabs.com

---

## Local Testing (Optional)

To preview the landing page locally before deploying:

```bash
cd /home/everydai-labs/agent/landing-page
python3 -m http.server 8000
# Open http://localhost:8000 in your browser
```

Or use npm:
```bash
npm run serve
```

---

## Files Included

- `index.html` — Main landing page
- `styles.css` — Professional dark theme styling
- `package.json` — Project metadata (unused for static site)
- `_redirects` — Cloudflare Pages routing configuration
- `.gitignore` — Git ignore rules
- `.git/` — Local git repository with initial commit
