FROM node:22.21.1-alpine3.21

WORKDIR /app

RUN corepack enable

COPY package.json pnpm-lock.yaml pnpm-workspace.yaml ./
COPY api/package.json ./api/package.json
COPY ui/package.json ./ui/package.json

RUN pnpm install --frozen-lockfile

COPY . .

WORKDIR /app/api

EXPOSE 3001

CMD ["pnpm", "start:dev"]