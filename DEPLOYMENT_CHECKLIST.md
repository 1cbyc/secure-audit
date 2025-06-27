# 🚀 Quick Deployment Checklist

## ✅ Pre-deployment (Done)
- [x] Frontend builds successfully
- [x] Backend builds successfully  
- [x] CORS configured for production domains
- [x] API configuration uses environment variables
- [x] _redirects file created for Cloudflare Pages

## 🔧 Backend Deployment (Next Step)

### Option 1: Railway (Recommended - Free tier available)
1. Go to [Railway.app](https://railway.app)
2. Connect your GitHub repository
3. Set root directory to `backend`
4. Add environment variables:
   - `PORT`: `3001`
   - `NODE_ENV`: `production`
5. Deploy and get the URL (e.g., `https://secure-audit-backend-production.up.railway.app`)

### Option 2: Render (Free tier available)
1. Go to [Render.com](https://render.com)
2. Create new Web Service
3. Connect your repository
4. Set root directory to `backend`
5. Build command: `npm install && npm run build`
6. Start command: `npm start`

## 🌐 Frontend Deployment (Cloudflare Pages)

1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com)
2. Navigate to Pages → Create a project
3. Connect your GitHub repository
4. Configure build settings:
   - **Framework preset**: Vite
   - **Build command**: `npm run build`
   - **Build output directory**: `dist`
   - **Root directory**: `frontend`
5. Add environment variable:
   - `VITE_API_URL`: `https://your-backend-url.com/api`
6. Deploy

## 🔗 Custom Domain Setup

1. In Cloudflare Pages project settings
2. Go to Custom domains
3. Add: `secure-audit.nsisonglabs.xyz`
4. Configure DNS as instructed

## 🧪 Testing

1. Visit your deployed frontend
2. Try analyzing a sample contract
3. Check browser console for errors
4. Test API endpoints directly

## 📞 Support

If you encounter issues:
1. Check Cloudflare Pages build logs
2. Check backend deployment logs
3. Test API with curl/Postman
4. Review browser network tab for errors 