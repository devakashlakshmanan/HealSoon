# HealSoon Workspace

## Overview

HealSoon is a fully functional, AI-driven hospital emergency orchestration and resource management system. Built with React + Vite frontend (orange/white UI) and Express backend with PostgreSQL.

## Stack

- **Monorepo tool**: pnpm workspaces
- **Node.js version**: 24
- **Package manager**: pnpm
- **TypeScript version**: 5.9
- **API framework**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod, `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Build**: esbuild (CJS bundle)
- **Frontend**: React + Vite, Tailwind CSS v4, Recharts, Framer Motion, Wouter, shadcn/ui
- **UI Theme**: Orange (#f97316) and white — medical emergency command center aesthetic

## Architecture

### Frontend (artifacts/healsoon)
- Pages: Dashboard, Emergency Triage, ICU & Beds, Patients, Resources, AI Predictions, Alerts Center
- Real-time data with React Query (auto-refresh 10-30s)
- Orange sidebar navigation with white content area
- shadcn/ui components, Recharts charts

### Backend (artifacts/api-server)
Routes:
- `/api/dashboard/summary` — aggregated KPIs
- `/api/dashboard/real-time` — live stats + hourly inflow
- `/api/patients` — CRUD, status filtering
- `/api/beds` — bed grid, ward stats, allocation
- `/api/triage` — emergency queue with AI severity scoring
- `/api/resources` — supply/equipment tracking
- `/api/predictions/demand` — 24h resource forecasting
- `/api/predictions/risk-zones` — emergency hotspot zones
- `/api/predictions/patient-outcomes` — AI outcome predictions
- `/api/alerts` — alert management + resolve

### Database Tables
- `patients` — patient records with vitals (jsonb)
- `beds` — bed map with ward/type/status
- `triage` — emergency queue with AI assessment (jsonb)
- `resources` — supply and equipment inventory
- `alerts` — critical alerts with resolve workflow

## Key Commands

- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- `pnpm --filter @workspace/api-server run dev` — run API server locally
- `pnpm --filter @workspace/healsoon run dev` — run frontend locally

## Features
- Real-time dashboard with live emergency inflow charts
- AI-powered triage with severity scoring and survival probability
- ICU/Bed allocation with visual ward grid
- Resource management with shortage alerts
- 24h demand predictions and risk zone analysis
- Critical alerts center with resolve workflow
- Auto-refreshing all critical data (10-30 second intervals)
