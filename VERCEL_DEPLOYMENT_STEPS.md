# Step-by-Step Vercel Deployment Guide

## Current Issue
You're trying to deploy from the root directory, but your frontend is in the `frontend` folder.

## Solution: Configure Vercel Settings

### On the Vercel "New Project" Page:

1. **Root Directory** (IMPORTANT!):
   - Click the "Edit" button next to "Root Directory"
   - Change from `./` to: `frontend`
   - This tells Vercel where your Next.js app is located

2. **Application Preset**:
   - Change from `Other` to: `Next.js`
   - Vercel will auto-detect Next.js and configure it properly

3. **Build and Output Settings**:
   - **Build Command**: Should auto-fill to `npm run build` (or `cd frontend && npm run build`)
   - **Output Directory**: Should be `out` (since you have `output: 'export'` in next.config.ts)
   - **Install Command**: Should be `npm install` (or `cd frontend && npm install`)

4. **Environment Variables** (Add these):
   - Click "+ Add More" to add each variable:
   
   **Required Variables:**
   - `NEXT_PUBLIC_API_URL` = `https://your-backend-url.railway.app` (you'll add this after deploying backend)
   - `NEXT_PUBLIC_RECAPTCHA_SITE_KEY` = Your reCAPTCHA site key (if you have one)

5. **Click "Deploy"**

---

## Alternative: Use vercel.json (Easier Method)

I've created a `vercel.json` file in your root directory. If Vercel still doesn't detect it automatically:

1. **Root Directory**: Set to `frontend` (still important!)
2. Vercel should read the `vercel.json` file and use those settings

---

## If GitHub Repo Doesn't Show in Vercel:

1. **Check GitHub Connection**:
   - Go to Vercel Dashboard → Settings → Git
   - Make sure your GitHub account is connected
   - Click "Connect GitHub" if needed

2. **Refresh the Import Page**:
   - Sometimes you need to refresh the page
   - Or go to Dashboard → "Add New..." → "Project" → "Import Git Repository"

3. **Check Repository Visibility**:
   - Make sure your GitHub repo is public OR
   - Grant Vercel access to your private repos

4. **Manual Import**:
   - If it still doesn't show, you can:
     - Click "Import Git Repository"
     - Paste your GitHub URL: `https://github.com/saliieey/Nicorai-website`
     - Vercel will import it

---

## After Frontend Deployment:

1. You'll get a URL like: `https://nicorai-website.vercel.app`
2. **Next Step**: Deploy your backend to Railway (see guide below)

---

## Backend Deployment (Railway):

1. Go to [railway.app](https://railway.app)
2. Sign up with GitHub
3. Click "New Project" → "Deploy from GitHub repo"
4. Select: `saliieey/Nicorai-website`
5. **Root Directory**: Set to `nicorai-api-gateway`
6. **Start Command**: `npm start`
7. Add environment variables (see below)
8. Deploy → Get your backend URL

**Backend Environment Variables:**
- `PORT` = `3000` (or leave empty, Railway auto-assigns)
- `FRONTEND_ORIGIN` = `https://nicorai-website.vercel.app` (your Vercel frontend URL)
- `REDIS_URL` = (optional - can add later)
- `N8N_WEBHOOK_URL` = Your webhook URL
- `RECAPTCHA_SECRET_KEY` = Your reCAPTCHA secret
- `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS`
- `EMAIL_TO_ADDRESS`, `EMAIL_FROM_ADDRESS`

---

## Update Frontend with Backend URL:

1. Go back to Vercel Dashboard
2. Select your project
3. Go to "Settings" → "Environment Variables"
4. Add/Update: `NEXT_PUBLIC_API_URL` = Your Railway backend URL
5. Click "Redeploy" to apply changes

---

## Quick Checklist:

- [ ] Root Directory set to `frontend` in Vercel
- [ ] Application Preset set to `Next.js`
- [ ] Build Command: `npm run build`
- [ ] Output Directory: `out`
- [ ] Environment variables added
- [ ] Frontend deployed successfully
- [ ] Backend deployed to Railway
- [ ] Frontend updated with backend URL
- [ ] Test the deployed site!

---

## Troubleshooting:

**If build fails:**
- Check that Root Directory is `frontend`
- Make sure `package.json` is in the `frontend` folder
- Check build logs in Vercel dashboard

**If GitHub repo doesn't show:**
- Disconnect and reconnect GitHub in Vercel settings
- Make sure repo is accessible
- Try manual import with URL

**If site doesn't work:**
- Check environment variables are set correctly
- Verify backend URL is correct
- Check browser console for errors

