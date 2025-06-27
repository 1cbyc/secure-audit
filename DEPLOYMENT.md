# Deployment Guide

## Frontend Deployment (Cloudflare Pages)

### Prerequisites
- Cloudflare account
- Git repository connected to Cloudflare Pages

### Steps

1. **Build the frontend locally to test:**
   ```bash
   cd frontend
   npm install
   npm run build
   ```

2. **Deploy to Cloudflare Pages:**
   - Go to Cloudflare Dashboard → Pages
   - Create a new project
   - Connect your Git repository
   - Set build settings:
     - **Framework preset:** Vite
     - **Build command:** `npm run build`
     - **Build output directory:** `dist`
     - **Root directory:** `frontend`
   - Set environment variables:
     - `VITE_API_URL`: `https://your-backend-url.com/api`

3. **Custom domain setup:**
   - Add custom domain: `secure-audit.nsisonglabs.xyz`
   - Configure DNS settings as instructed by Cloudflare

## Backend Deployment

### Option 1: Railway (Recommended)

1. **Prepare the backend:**
   ```bash
   cd backend
   npm install
   npm run build
   ```

2. **Deploy to Railway:**
   - Connect your GitHub repository to Railway
   - Set the root directory to `backend`
   - Set environment variables:
     - `PORT`: `3001`
     - `NODE_ENV`: `production`
     - `DATABASE_URL`: Your PostgreSQL connection string

3. **Get the deployment URL** and update the frontend's `VITE_API_URL`

### Option 2: Render

1. **Create a new Web Service**
2. **Connect your repository**
3. **Configure:**
   - **Build Command:** `npm install && npm run build`
   - **Start Command:** `npm start`
   - **Root Directory:** `backend`

### Option 3: Vercel

1. **Deploy as a Node.js function**
2. **Set environment variables**
3. **Configure the build settings**

## Environment Variables

### Frontend (.env.production)
```
VITE_API_URL=https://your-backend-url.com/api
```

### Backend
```
PORT=3001
NODE_ENV=production
DATABASE_URL=your-postgresql-connection-string
JWT_SECRET=your-jwt-secret
```

## Testing the Deployment

1. **Test the backend API:**
   ```bash
   curl -X POST https://your-backend-url.com/api/contracts/analyze \
     -H "Content-Type: application/json" \
     -d '{"contractCode":"contract Test {}","options":{}}'
   ```

2. **Test the frontend:**
   - Visit your deployed frontend URL
   - Try analyzing a sample contract
   - Check browser console for any errors

## Troubleshooting

### Common Issues

1. **CORS errors:**
   - Ensure backend CORS is configured for your frontend domain
   - Check that the API URL is correct

2. **Build failures:**
   - Check that all dependencies are installed
   - Verify TypeScript compilation

3. **API connection issues:**
   - Verify the backend is running
   - Check environment variables
   - Test API endpoints directly

### Debugging

1. **Check Cloudflare Pages logs**
2. **Check backend deployment logs**
3. **Use browser developer tools to inspect network requests**
4. **Test API endpoints with tools like Postman or curl** 