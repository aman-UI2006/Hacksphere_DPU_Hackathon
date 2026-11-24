# KrushiMitra Backend

Node.js/Express API for the KrushiMitra agricultural application. The codebase includes farmer and activity data workflows, mandi-price services, AI-assisted interactions, authentication integrations, notifications, and scheduled jobs.

> Development/hackathon project. Provider integrations depend on environment configuration. Review security and deployment settings before public or production use.

## Features

- Farmer profile and activity endpoints.
- MongoDB persistence and database initialization utilities.
- Firebase identity verification and Google OAuth integration.
- Mandi-price retrieval and scheduled mandi-price / scheme jobs.
- AI-assisted farmer chat and plant-identification integration.
- Optional email, SMS/voice, and text-to-speech integrations.
- Structured logging and diagnostic scripts.

## Stack

Node.js, Express, MongoDB, Firebase Admin, Google authentication libraries, Groq SDK, Winston, node-cron, Jest, and Supertest.

## Setup

### Requirements
- Node.js 20 LTS recommended
- npm
- MongoDB connection details
- Credentials for any external integrations you enable

### Environment configuration

The server loads `.env` from the **parent directory** of this folder. In a normal clone, copy the repository-root example file:

```bash
# Run from the repository root
cp .env.example .env
```

Edit the values locally. Do not commit the resulting `.env`, service-account files, tokens, or API keys.

### Install and run

```bash
cd KrushiMitra-Backend
npm ci
npm run dev
```

The port is controlled by `PORT` in the environment (the supplied example uses `3001`).

## Background jobs

```bash
npm run jobs
npm run jobs:run-once
```

The scheduler includes mandi-price and agricultural-scheme jobs. Verify upstream feed availability and credentials before relying on scheduled results.

## Tests

```bash
npm test
npm run test:plan
npm run test:connections
npm run test:logging
```

Some tests require a reachable MongoDB instance and configured integrations. Record the exact command and environment when reporting test results.

## API documentation

- [API contract](API_CONTRACT.md)
- [Multi-user database connections](MULTI_USER_CONNECTIONS.md)
- [Structured logging](STRUCTURED_LOGGING.md)
- [Background jobs](background-jobs.md)
- [Security checklist](SECURITY_CHECKLIST.md)
- [MongoDB setup](MONGODB_ATLAS_USERS_SETUP.md)

The API contract contains illustrative examples; confirm the deployed base URL and actual route behavior against the running service.

## Security checklist

- Use least-privilege MongoDB credentials and restrict Atlas network access.
- Replace wildcard CORS with an explicit frontend-origin allowlist.
- Protect OAuth, Firebase service-account, AI-provider, email, and telephony secrets.
- Validate authentication and authorization on every sensitive route.
- Avoid exposing diagnostic scripts, logs, and administrative operations publicly.

## Status

Prototype / active development. The presence of an integration or setup document does not by itself prove that the integration is configured, tested, or production-ready.
