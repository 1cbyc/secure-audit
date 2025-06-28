# Environment Variables Configuration

## Frontend (.env.local)

Create a file called `.env.local` in the `frontend/` directory with the following content:

```env
# Frontend Environment Variables
# Copy this file to .env.local for local development

# API Configuration
VITE_API_URL=http://localhost:3001/api

# Build Configuration
VITE_APP_NAME=Secure Audit
VITE_APP_VERSION=1.0.0

# Feature Flags
VITE_ENABLE_ANALYTICS=false
VITE_ENABLE_DEBUG_MODE=true

# External Services (if needed in the future)
# VITE_GOOGLE_ANALYTICS_ID=your-ga-id
# VITE_SENTRY_DSN=your-sentry-dsn

# Development Settings
VITE_DEV_MODE=true
VITE_LOG_LEVEL=debug
```

## Backend (.env)

Create a file called `.env` in the `backend/` directory with the following content:

```env
# Backend Environment Variables
# Copy this file to .env for local development

# Server Configuration
PORT=3001
NODE_ENV=development

# Database Configuration (PostgreSQL)
DATABASE_URL=postgres://username:password@localhost:5432/secure_audit
DB_HOST=localhost
DB_PORT=5432
DB_NAME=secure_audit
DB_USER=postgres
DB_PASSWORD=your_password

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
JWT_EXPIRES_IN=24h

# CORS Configuration
CORS_ORIGIN=http://localhost:3000,https://secure-audit.nsisonglabs.xyz

# Security
BCRYPT_ROUNDS=12

# Logging
LOG_LEVEL=debug
LOG_FILE=logs/app.log

# External Services (if needed)
# REDIS_URL=redis://localhost:6379
# SENTRY_DSN=your-sentry-dsn

# Development Settings
ENABLE_SWAGGER=true
ENABLE_DEBUG_MODE=true
```

## Production Environment Variables

For production deployment, set these environment variables in your hosting platform:

### Frontend (Cloudflare Pages)
- `VITE_API_URL`: `https://secure-audit-backend.onrender.com/api`

### Backend (Render)
- `PORT`: `3001`
- `NODE_ENV`: `production`
- `DATABASE_URL`: Your production PostgreSQL connection string
- `JWT_SECRET`: Your production JWT secret
- `CORS_ORIGIN`: `https://secure-audit.nsisonglabs.xyz`

## Important Notes

1. **Never commit `.env` files to Git** - they contain sensitive information
2. **Use strong, unique secrets** for production
3. **Rotate secrets regularly** for security
4. **Use different databases** for development and production
5. **Enable HTTPS** in production environments

## File Structure

```
secure-audit/
├── frontend/
│   ├── .env.local          # Local development (not in git)
│   └── .env.example        # Example file (in git)
├── backend/
│   ├── .env                # Local development (not in git)
│   └── .env.example        # Example file (in git)
└── .gitignore              # Should include .env files
``` 