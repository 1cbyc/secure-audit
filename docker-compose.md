version: '3.8'

services:
  # Frontend
  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    ports:
      - "3000:3000"
    environment:
      - REACT_APP_API_URL=http://localhost:5000/api
      - REACT_APP_ENVIRONMENT=development
    volumes:
      - ./frontend:/app
      - /app/node_modules
    depends_on:
      - backend

  # Backend API
  backend:
    build:
      context: ./backend
      dockerfile: Dockerfile
    ports:
      - "5000:5000"
    environment:
      - NODE_ENV=development
      - DATABASE_URL=postgresql://postgres:password@postgres:5432/secure_audit
      - REDIS_URL=redis://redis:6379
      - JWT_SECRET=your-super-secret-jwt-key-here
      - RATE_LIMIT_WINDOW=15
      - RATE_LIMIT_MAX=100
    volumes:
      - ./backend:/app
      - /app/node_modules
    depends_on:
      - postgres
      - redis

  # PostgreSQL Database
  postgres:
    image: postgres:15-alpine
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_DB=secure_audit
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=password
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./backend/database/init.sql:/docker-entrypoint-initdb.d/init.sql

  # Redis Cache
  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data

  # Nginx Reverse Proxy (Production)
  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf
      - ./nginx/ssl:/etc/nginx/ssl
    depends_on:
      - frontend
      - backend
    profiles:
      - production

volumes:
  postgres_data:
  redis_data:

<!---->

version: "3.9"
services:
postgres:
image: postgres:14
container_name: secureaudit_postgres
restart: unless-stopped
ports:
- "5432:5432"
environment:
POSTGRES_DB: secure_audit
POSTGRES_USER: postgres
POSTGRES_PASSWORD: postgres123
volumes:
- postgres_data:/var/lib/postgresql/data

redis:
image: redis:7
container_name: secureaudit_redis
restart: unless-stopped
ports:
- "6379:6379"

backend:
build:
context: ./backend
container_name: secureaudit_backend
restart: unless-stopped
ports:
- "5000:5000"
environment:
PORT: 5000
NODE_ENV: development
JWT_SECRET: devsecretkey
JWT_EXPIRES_IN: 1d
DB_HOST: postgres
DB_PORT: 5432
DB_USER: postgres
DB_PASSWORD: postgres123
DB_NAME: secure_audit
REDIS_URL: redis://redis:6379
depends_on:
- postgres
- redis

frontend:
build:
context: ./frontend
container_name: secureaudit_frontend
ports:
- "3000:3000"
stdin_open: true
tty: true
environment:
- CHOKIDAR_USEPOLLING=true
depends_on:
- backend

volumes:
postgres_data:
