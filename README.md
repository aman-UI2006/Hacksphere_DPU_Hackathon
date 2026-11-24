# KrushiMitra — Agricultural Assistant Backend

KrushiMitra is an agricultural application backend designed to support farmer profiles, activity records, mandi-price information, AI-assisted interactions, and related farmer services.

This repository contains the Node.js/Express backend, integration code, operational documentation, and a nested `KrushiMitra-Backend/` project directory.

## Capabilities represented in the codebase

- Farmer profile and activity management backed by MongoDB.
- Firebase-based identity verification and Google OAuth integration.
- Mandi-price retrieval and scheduled price-processing jobs.
- AI-assisted farmer interactions using configured model providers.
- Plant-identification integration.
- Notification and communication integrations, including email and SMS/voice providers.
- Structured application/database logging and operational scripts.

Provider features require valid credentials and may be disabled when their environment variables are not configured.

## Technology

- Node.js and Express
- MongoDB / MongoDB Atlas
- Firebase Admin and Google authentication libraries
- Groq and other optional AI/communication SDKs
- Winston logging and node-cron scheduled jobs
- Jest and Supertest tooling

## Repository guide

- `KrushiMitra-Backend/` — backend project copy and its package scripts
- `API_CONTRACT.md` — API contract draft and request/response examples
- `GOOGLE_OAUTH_SETUP_GUIDE.md` — OAuth configuration notes
- `KrushiMitra-Backend/MULTI_USER_CONNECTIONS.md` — database connection-role design
- `KrushiMitra-Backend/STRUCTURED_LOGGING.md` — logging details
- `KrushiMitra-Backend/background-jobs.md` — scheduled job notes
- `KrushiMitra-Backend/SECURITY_CHECKLIST.md` — security review checklist

## Local setup

Use the nested backend project directory. Its server loads the environment file from the repository root.

### Prerequisites
- Node.js 20 LTS recommended
- npm
- A MongoDB database
- Firebase project credentials for enabled authentication flows
- Optional provider credentials for AI, email, SMS/voice, and plant-identification features

### Install

```bash
git clone https://github.com/aman-UI2006/Hacksphere_DPU_Hackathon.git
cd Hacksphere_DPU_Hackathon
cp .env.example .env
cd KrushiMitra-Backend
npm ci
```

Edit the root `.env` with your own development values. Keep service-account JSON files and all real credentials outside Git.

### Start the API

```bash
npm run dev
```

The example environment config uses port `3001`; the actual port is controlled by `PORT`.

### Background jobs

```bash
npm run jobs
# Run scheduled jobs once where supported by the script:
npm run jobs:run-once
```

### Tests

```bash
npm test
npm run test:plan
npm run test:connections
npm run test:logging
```

These scripts exercise different parts of the project and may require a configured database and provider credentials. A passing local run should be reported with the exact environment and command used.

## API documentation

See [API_CONTRACT.md](API_CONTRACT.md) for the documented routes and example payloads. Treat the example base URL and sample records in that document as placeholders; configure the real API host and authentication settings for your deployment.

## Security notes

- Restrict MongoDB network access and use least-privilege database users.
- Replace wildcard CORS settings with an explicit allowlist before deployment.
- Protect Firebase service-account credentials, OAuth secrets, API keys, and session secrets.
- Do not expose debug scripts, logs, or database administration endpoints publicly.
- Review authentication, authorization, input validation, rate limiting, and data retention before production use.

## Status

Hackathon / development codebase. The repository documents intended integrations and workflows; verify each provider integration and test path in a configured environment before describing it as production-ready.
