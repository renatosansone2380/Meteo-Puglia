# Workspace

## Overview

pnpm workspace monorepo using TypeScript. Each package manages its own dependencies.

## Artifacts

- **meteo-box** (`/`): GeoTaras Meteo Box — widget meteo per geotaras.it con spaghi ensemble (GFS GEFS / ECMWF IFS) a 500 e 850 hPa, previsioni meteomarine (onde, vento, stato del mare) e nowcasting (satellite, radar, fulminazioni).
- **api-server** (`/api`): shared Express API server (currently only health endpoint).
- **mockup-sandbox** (`/__mockup`): canvas/design preview sandbox.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)
- **Frontend (meteo-box)**: React + Vite + Tailwind v4 + shadcn/ui + Recharts

## Data sources used by meteo-box

- Open-Meteo Ensemble API (https://ensemble-api.open-meteo.com) — ECMWF IFS 0.25° + GFS GEFS 0.25°
- Open-Meteo Marine API (WAVEWATCH III)
- Open-Meteo Forecast API (vento 10 m)
- Windy.com embed (satellite, radar, thunder)

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally
- `pnpm --filter @workspace/meteo-box run dev` — run the meteo widget locally

See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details.
