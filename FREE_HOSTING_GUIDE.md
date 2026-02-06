# Free Hosting Guide for NicorAI Website

## Project Analysis

Your project consists of:
- **Frontend**: Next.js 15 application (configured for static export)
- **Backend**: Node.js/Express API with Redis, email services, and reCAPTCHA

## 🏆 Best Free Hosting Options

### Option 1: Vercel (RECOMMENDED - Best for Next.js)

**Why Vercel?**
- Made by the creators of Next.js - perfect integration
- Free tier is very generous
- Automatic deployments from GitHub
- Free subdomain: `yourproject.vercel.app`
- Can host both frontend and backend (using serverless functions)

**Free Tier Includes:**
- Unlimited deployments
- 100GB bandwidth/month
- Serverless functions (for your API)
- Automatic SSL certificates
- Custom domain support

**Steps to Deploy:**

1. **Push your code to GitHub** (if not already)
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin YOUR_GITHUB_REPO_URL
   git push -u origin main
   ```

2. **Deploy Frontend:**
   - Go to [vercel.com](https://vercel.com)
   - Sign up with GitHub
   - Click "New Project"
   - Import your repository
   - Set **Root Directory** to `frontend`
   - Add environment variables:
     - `NEXT_PUBLIC_API_URL` = Your backend URL (you'll get this after deploying backend)
     - `NEXT_PUBLIC_RECAPTCHA_SITE_KEY` = Your reCAPTCHA site key
   - Click "Deploy"
   - You'll get a URL like: `https://nicorai-website.vercel.app`

3. **Deploy Backend as Serverless Functions:**
   - Create a new Vercel project
   - Set **Root Directory** to `nicorai-api-gateway`
   - Add environment variables:
     - `PORT` = 3000 (or leave empty, Vercel handles it)
     - `FRONTEND_ORIGIN` = Your frontend Vercel URL
     - `REDIS_URL` = (optional, can use Upstash free Redis)
     - `N8N_WEBHOOK_URL` = Your n8n webhook URL
     - `RECAPTCHA_SECRET_KEY` = Your reCAPTCHA secret
     - `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS`
     - `EMAIL_TO_ADDRESS`, `EMAIL_FROM_ADDRESS`
   - Deploy

**Alternative: Convert Backend to Vercel Serverless Functions**
- You may need to refactor your Express app slightly for Vercel's serverless format
- Or use the approach below for backend

---

### Option 2: Vercel (Frontend) + Railway (Backend)

**Why this combo?**
- Vercel for frontend (best Next.js support)
- Railway for backend (easier Node.js deployment)

**Railway Backend Setup:**
1. Go to [railway.app](https://railway.app)
2. Sign up with GitHub
3. Click "New Project" → "Deploy from GitHub repo"
4. Select your repository
5. Set **Root Directory** to `nicorai-api-gateway`
6. Add environment variables (same as above)
7. Railway gives you a URL like: `https://your-api.up.railway.app`
8. Use this URL as `NEXT_PUBLIC_API_URL` in your Vercel frontend

**Railway Free Tier:**
- $5 free credit/month
- Usually enough for small projects
- Auto-deploys from GitHub

---

### Option 3: Netlify (Frontend) + Render (Backend)

**Netlify Frontend:**
1. Go to [netlify.com](https://netlify.com)
2. Sign up with GitHub
3. "Add new site" → "Import an existing project"
4. Select your repo
5. Build settings:
   - **Base directory**: `frontend`
   - **Build command**: `npm run build`
   - **Publish directory**: `frontend/out`
6. Add environment variables
7. Deploy → Get URL: `https://yourproject.netlify.app`

**Render Backend:**
1. Go to [render.com](https://render.com)
2. Sign up with GitHub
3. "New" → "Web Service"
4. Connect your repo
5. Settings:
   - **Root Directory**: `nicorai-api-gateway`
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
6. Add environment variables
7. Deploy → Get URL: `https://your-api.onrender.com`

**Render Free Tier:**
- Free tier available (spins down after 15 min inactivity)
- Good for portfolio projects

---

### Option 4: All-in-One: Render

**Deploy Both on Render:**
1. Deploy frontend as "Static Site"
2. Deploy backend as "Web Service"
3. Both get free subdomains

---

## 🎯 My Recommendation

**Use Vercel for Frontend + Railway for Backend**

**Why?**
- ✅ Vercel is perfect for Next.js (made by Next.js creators)
- ✅ Railway is easy for Node.js APIs
- ✅ Both have good free tiers
- ✅ Both auto-deploy from GitHub
- ✅ Professional URLs for your portfolio

**Your Portfolio Links:**
- Frontend: `https://nicorai-website.vercel.app`
- Backend API: `https://nicorai-api.up.railway.app`

---

## 📝 Quick Start Checklist

1. [ ] Push code to GitHub
2. [ ] Deploy frontend to Vercel
3. [ ] Deploy backend to Railway
4. [ ] Set environment variables
5. [ ] Update frontend `NEXT_PUBLIC_API_URL` with backend URL
6. [ ] Test your deployed site
7. [ ] Add custom domain (optional)

---

## 🔧 Environment Variables Checklist

### Frontend (Vercel):
- `NEXT_PUBLIC_API_URL` = Your backend URL
- `NEXT_PUBLIC_RECAPTCHA_SITE_KEY` = Your reCAPTCHA site key

### Backend (Railway/Render):
- `PORT` = 3000 (or leave empty)
- `FRONTEND_ORIGIN` = Your frontend URL
- `REDIS_URL` = (optional - use Upstash free Redis if needed)
- `N8N_WEBHOOK_URL` = Your webhook URL
- `RECAPTCHA_SECRET_KEY` = Your reCAPTCHA secret
- `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS`
- `EMAIL_TO_ADDRESS`, `EMAIL_FROM_ADDRESS`

---

## 🆓 Free Redis Options (if needed)

- **Upstash**: Free tier with 10K commands/day
- **Redis Cloud**: Free tier available
- **Railway**: Can add Redis service (uses free credits)

---

## 📚 Additional Resources

- [Vercel Documentation](https://vercel.com/docs)
- [Railway Documentation](https://docs.railway.app)
- [Netlify Documentation](https://docs.netlify.com)
- [Render Documentation](https://render.com/docs)

---

## 🚀 Need Help?

If you need help with the actual deployment process, I can:
1. Help you set up the deployment configurations
2. Create deployment scripts
3. Refactor code if needed for specific platforms
4. Set up environment variable templates

Let me know which option you'd like to proceed with!

