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

### Scaffold a new project

```bash
bun create rnldsalili/cf-hono-react-template <project-name>
```

The interactive setup script will prompt for your project name, replace config placeholders, install dependencies, and initialise a fresh git repository.

### After scaffolding

**1. Configure environment variables**

```bash
cp apps/api/.dev.vars.example apps/api/.dev.vars
cp apps/admin/.env.example apps/admin/.env
```

**2. Create Cloudflare D1 databases**

```bash
bunx wrangler d1 create <project-name>-dev
bunx wrangler d1 create <project-name>-prod
```

Copy the `database_id` values printed by the commands above into `apps/api/wrangler.jsonc`.

**3. Apply DB migrations locally**

```bash
cd apps/api && bunx wrangler d1 migrations apply <project-name>-dev --local
```

**4. Start development servers**

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
