# 🚀 Render Deployment Guide (Free & Easy)

## Why Render?
- ✅ **Free tier**: 750 hours/month
- ✅ **Easy setup**: Connect GitHub, deploy in minutes
- ✅ **Automatic deployments**: Updates on every push
- ✅ **Custom domains**: Free SSL certificates
- ✅ **No credit card required** for free tier

## Step-by-Step Deployment

### 1. Prepare Your Repository
The repository is already configured with proper build scripts.

### 2. Deploy to Render

1. **Go to [Render.com](https://render.com)**
2. **Sign up with GitHub** (free)
3. **Click "New +" → "Web Service"**
4. **Connect your GitHub repository**
5. **Configure the service:**

   **Basic Settings:**
   - **Name**: `secure-audit-backend`
   - **Root Directory**: `backend` ⚠️ **IMPORTANT: Set this to `backend`**
   - **Runtime**: `Node`
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm start`

   **Environment Variables:**
   - `PORT`: `3001`
   - `NODE_ENV`: `production`

6. **Click "Create Web Service"**

### 3. Alternative: Deploy from Root Directory

If the above doesn't work, try this configuration:

   **Basic Settings:**
   - **Name**: `secure-audit-backend`
   - **Root Directory**: `.` (root of repository)
   - **Runtime**: `Node`
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm start`

### 4. Get Your Backend URL
After deployment, you'll get a URL like:
`https://secure-audit-backend.onrender.com`

### 5. Update Frontend Configuration
In your Cloudflare Pages environment variables:
- `VITE_API_URL`: `https://secure-audit-backend.onrender.com/api`

## 🧪 Testing Your Deployment

### Test Backend Health:
```bash
curl https://secure-audit-backend.onrender.com/api/health
```

### Test API Endpoint:
```bash
curl -X POST https://secure-audit-backend.onrender.com/api/analysis/analyze \
  -H "Content-Type: application/json" \
  -d '{"contractCode":"contract Test {}","options":{}}'
```

## ⚠️ Important Notes

### Free Tier Limitations:
- **Sleep after 15 minutes** of inactivity
- **First request** after sleep takes 10-30 seconds to wake up
- **750 hours/month** (about 31 days of continuous running)

### Performance Tips:
- The first request after sleep will be slow
- Subsequent requests will be fast
- Consider upgrading to paid plan for production use

## 🔧 Troubleshooting

### Common Issues:
1. **Build fails**: Check that `npm run build` works locally
2. **Port issues**: Make sure `PORT` environment variable is set
3. **CORS errors**: Backend is already configured for your domains
4. **TypeScript errors**: Type definitions are now in dependencies

### Debug Steps:
1. Check Render deployment logs
2. Test API endpoints directly
3. Verify environment variables are set correctly

## 🎉 Success!
Once deployed, your backend will be available at:
`https://secure-audit-backend.onrender.com`

Update your frontend's `VITE_API_URL` and deploy to Cloudflare Pages! 