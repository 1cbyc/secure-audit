# Deployment Guide

This document provides step-by-step instructions for deploying the Secure Audit application.

## Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Docker (optional, for containerized deployment)
- Access to required environment variables (see `.env.example`)

## 1. Clone the Repository

```bash
git clone https://github.com/1cbyc/secure-audit.git
cd secure-audit
```

## 2. Install Dependencies

```bash
npm install
# or
yarn install
```

## 3. Configure Environment Variables

Copy the example environment file and update values as needed:

```bash
cp .env.example .env
```

Edit `.env` to set database credentials, API keys, and other secrets.

## 4. Build the Application

```bash
npm run build
# or
yarn build
```

## 5. Run Database Migrations

```bash
npm run migrate
# or
yarn migrate
```

## 6. Start the Application

```bash
npm start
# or
yarn start
```

The application should now be running at `http://localhost:3000`.

## 7. (Optional) Deploy with Docker

Build and run the Docker container:

```bash
docker build -t secure-audit .
docker run -d -p 3000:3000 --env-file .env secure-audit
```

## 8. Troubleshooting

- Check logs with `npm run logs` or `docker logs <container_id>`.
- Ensure all environment variables are set correctly.
- Verify database connectivity.

## 9. Additional Resources

- [Configuration Reference](./CONFIGURATION.md)
- [FAQ](./FAQ.md)
- [Support](mailto:ei@nsisong.com)
