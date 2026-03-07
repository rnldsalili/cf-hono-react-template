# cf-hono-react-template

A monorepo template for building full-stack applications with Cloudflare Workers, Hono, and React.

## Stack

| Layer | Technology |
| :--- | :--- |
| API runtime | Cloudflare Workers (Wrangler) |
| API framework | Hono v4 |
| Database | Cloudflare D1 (SQLite) via Prisma 7 |
| Auth | Better Auth |
| Frontend | React 19 + TanStack Start |
| Routing | TanStack Router |
| Styling | Tailwind CSS v4 |
| UI components | Base UI + shadcn/ui |
| Package manager | Bun |

## Structure

```
apps/
  admin/   # TanStack Start frontend (port 3010)
  api/     # Hono + Cloudflare Workers backend (port 3000)
packages/
  api-client/        # Hono RPC client
  auth-client/       # Better Auth client
  ui/                # Shared component library
  constants/
  eslint-config/
  typescript-config/
```

## Getting Started

**1. Install dependencies**

```bash
bun install
```

**2. Configure environment**

```bash
# API
cp apps/api/.dev.vars.example apps/api/.dev.vars

# Admin
cp apps/admin/.env.example apps/admin/.env
```

**3. Start development servers**

```bash
bun run dev
```

## Commands

| Command | Description |
| :--- | :--- |
| `bun run dev` | Start all services in parallel |
| `bun run lint` | Lint all workspaces |
| `bun run lint:fix` | Fix lint errors |
| `bun run typecheck` | Type-check all workspaces |
| `bun run db:generate` | Regenerate Prisma client |
