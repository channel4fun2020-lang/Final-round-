<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

# NetCoop AI — project rules

- NetCoop AI was migrated from an external FastAPI + MongoDB archive into TanStack Start; the original Python files are not part of this repo. The TS engine lives in `src/lib/netcoop/` (types, validate, rules, agents, orchestrator, topology, converter, scenarios, db, service).
- All API endpoints live under `src/routes/api/v1/*` with the same paths as the source app (`/api/v1/...`); the SSE stream route is `/api/v1/diagnose/stream`. The frontend always calls relative `/api` paths from `src/lib/api.ts`.
- The app has no login by design (public single-tenant workbench, as in the source). The `incidents` table has anon SELECT/INSERT policies; do not add auth-gated rewrites of these routes without a decision to add login.
- The 13 seeded scenarios are static JSON in `src/lib/netcoop/data/` and the 5 sample uploads in `public/samples/`; they are bundled, not database rows.
- The uploaded-file converter supports JSON, YAML, CSV/TSV, Excel (.xlsx), Word (.docx), PDF (unpdf), and key=value text; it runs server-side on workerd — keep using pure-JS libs (yaml, xlsx, fflate, unpdf) there, no Node-only packages.
- Frontend pages are ported from the source React app under `src/pages/` and rendered by TanStack route files in `src/routes/`; the placeholder routes (/monitoring, /agents, /communication, /diagnostics, /scenarios) intentionally render the Dashboard, matching the source.
- Base UI copies of button/dialog/textarea live in `src/components/ui/baseui/` (used by the ported pages); `src/components/ui/*` stays the template shadcn set.
- Engine rules have vitest coverage in `src/test/netcoop-engine.test.ts` (scenario verdicts, validation, converter, compare verdicts); run `bunx vitest run` after touching `src/lib/netcoop/`.
