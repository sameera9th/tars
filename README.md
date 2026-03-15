# Tars Monorepo

## 🚀 Overview

Tars is a full-stack monorepo containing:
- `api/` - NestJS backend API
- `ui/` - Next.js frontend
- Docker Compose for local environment orchestration

The workspace is managed using `pnpm` workspaces and targets Node.js 22.21.1.

## 🧩 Folder Structure

```
code/
  api/           # NestJS backend service
  ui/            # Next.js frontend service
  docker-compose.yml
  package.json
  pnpm-lock.yaml
  pnpm-workspace.yaml

# optional:
# packages/     # shared packages (future / present)
```

## 📦 Tech Stack

- Backend: NestJS
- Frontend: Next.js
- Package Manager: pnpm
- Runtime: Node.js 22.21.1
- Containers: Docker + Docker Compose

## ✅ Prerequisites

Install these tools first:

- Node.js 22.21.1
- pnpm
- Docker Desktop (Docker Engine + Docker Compose)

Verify your environment:

```bash
node -v
pnpm -v
docker -v
docker compose version
```

## ⚙️ Setup (one-time)

```bash
cd code
pnpm install
```

## 🛠️ Development

### Run with Docker (recommended)

```bash
cd code
docker compose up --build
```

- UI: `http://localhost:3000`
- API: `http://localhost:3001`

### Run locally without Docker

From monorepo root (`code/`):

```bash
pnpm --filter api start:dev
pnpm --filter ui dev
```

## 🐳 Docker commands

- Start: `docker compose up`
- Build and start: `docker compose up --build`
- Stop: `docker compose down`
- Remove volumes: `docker compose down -v`

## 🌐 Environment variables

`ui` expects:

- `NEXT_PUBLIC_API_URL=http://localhost:3001`

`api` can use environment variables from `api/.env` (if present).

## 🧪 Testing

### API tests

```bash
cd code/api
pnpm test
```

### E2E tests (Nest + Jest)

```bash
cd code/api
pnpm test:e2e
```

## 🧾 Monorepo config

`pnpm-workspace.yaml`:

```yaml
packages:
  - 'api'
  - 'ui'
  - 'packages/*'
```

## 📌 Notes

- `api` and `ui` run as separate services in both Docker and local dev.
- Docker ports: UI = 3000, API = 3001.
- Root-level `package.json` bootstraps workspace commands and shared scripts.

## 🚧 Roadmap

Future improvements:

- Shared packages under `packages/`
- Database support for API
- CI/CD pipelines
- Production Docker images for API and UI

