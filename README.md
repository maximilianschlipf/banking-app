# Banking App Workshop – Root Runner

This root adds simple, one-place commands to run and prepare the demo app for your workshop.

## Setup Both Projects

- One-time (or after dependency changes):
  - `npm run setup`
    - Installs frontend dependencies in `banking-frontend/`
    - Builds backend modules and packages the server JAR in `banking-backend/`

## Quick Start (Local Dev)

- Prereqs: Node 18+ (or 20+), npm, Java 21+, Maven.
- Backend runs on `http://localhost:5005`, Frontend on `http://localhost:4200`.

Steps:

1. Install the root runner dependency:
   - `npm install` (installs `concurrently` only at the root)
2. (Optional) Bootstrap both projects:
   - `npm run setup`
3. Start both services:
   - `npm start`
   - Optional (English UI): `npm run start:en`

Notes:

- The frontend dev server targets `environment.api_url` which is already `http://localhost:5005` for development.
- If Maven is not available, use the Docker Compose option below.

## Docker Compose (No local Java/Angular toolchain)

Build and run both services in containers:

- `docker compose up --build`

This starts:

- Backend (Spring Boot) at `http://localhost:5005`
- Frontend (nginx) at `http://localhost:8080` using the DEV build (targets the backend on `localhost:5005`).

## Repo Structure

- `banking-backend/` – Spring Boot server (port 5005)
- `banking-frontend/` – Angular app (dev server 4200; prod build via nginx)
- `docker-compose.yml` – Containerized runner for both services
- `package.json` – Root runner scripts for local dev

## Workshop Tests

Intentionally omitted here so attendees can scaffold their own Playwright setup in a new `tests/` folder at the repo root.
