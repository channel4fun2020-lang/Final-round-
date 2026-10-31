# NetCoop AI migration roadmap

Source: netcoop-ai-full.zip (FastAPI + MongoDB + Vite/React). Target: TanStack Start + Lovable Cloud.

## Tasks
- [x] Enable Lovable Cloud
- [x] Migration: create `public.incidents` table (jsonb report/messages/topology/telemetry), grants, anon SELECT/INSERT RLS
- [x] Copy 13 scenario JSON files + 5 sample upload files into project
- [x] Port diagnosis engine to TS: types, validator, normalizer, 3 investigators, correlation, reporting, rules/confidence, topology, orchestrator
- [x] Port file converter to TS (JSON, YAML, CSV/TSV, xlsx, docx, pdf, key=value text)
- [x] Server routes: health, scenarios, scenarios/$id, diagnose, diagnose/stream (SSE), diagnose/upload, incidents (+messages, +rediagnose)
- [x] Port frontend: styles/design tokens, pages (Dashboard, Compare, IncidentHistory), components, TanStack Router routes for all 8 sidebar paths
- [x] Install deps: lucide-react, recharts, sonner, motion, date-fns, yaml, xlsx, unpdf, fflate (+ ui deps)
- [x] Port key tests to vitest and run
- [x] Verify end-to-end in browser: run scenario, streaming, upload, history, compare, rediagnose
- [x] Head metadata for every route
- [ ] Handoff: ask for existing incident records export (records pending — source incidents were not in the ZIP)
