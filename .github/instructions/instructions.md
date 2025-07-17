---
applyTo: "**"
---
# Todoee – Copilot Custom Instructions

## Project Overview  
Todoee is a **local-first, self-hosted PWA** task manager. It ships as a single Docker container, works fully offline, and syncs in real time once connectivity is restored. Core specs live in the [PRD](../docs/PRD.md) and [Architecture](../docs/ARCHITECTURE.md).

## Tech Stack (Authoritative)  
- **Frontend:** React + TypeScript (Vite).  
- **State:** Zustand.  
- **Styling/UI:** Tailwind CSS via Flowbite; respect `@apply` to keep class noise low.  
- **Persistence & Sync:** IndexedDB (Dexie) offline cache ➜ REST + WebSocket sync.  
- **Backend:** Fastify + Prisma + SQLite.  
- **Build & Dev:** pnpm, dev-container, GitHub Actions CI, Docker build.  
- **Testing:** Vitest/unit; Playwright end-to-end (wire up later phases).  

## Coding Guidelines  
- Prefer **functional components with hooks**; no class components.  
- Use TypeScript strict mode; enable `noUncheckedIndexedAccess`.  
- Keep components ≤ 200 LOC; extract pure helpers to `/lib`.  
- Adhere to **DRY & SOLID** but stay pragmatic—avoid over-abstraction.  
- Name things clearly: `PascalCase` for components/types, `camelCase` otherwise.  
- Co-locate tests: `ComponentName.test.tsx`.  
- Inline small SVG icons; lazy-load heavy assets.  

## Architectural Principles  
1. **Local-first:** All writes succeed offline, then sync.  
2. **Single source of truth:** SQLite on the server ≫ IndexedDB shadow.  
3. **Optimistic UI:** Update instantly, roll back on error.  
4. **Lean deps:** If vanilla JS/TS does it, skip another lib.  

## Dev Workflow & Tooling  
- Work in the **`devcontainer`**; Node 20-slim is baseline.  
- Use **feature-branch + PR**; one logical change per PR.  
- Run `pnpm lint && pnpm test` pre-push (CI will block otherwise).  
- Every PR must update the **CHANGELOG** and bump version via `semantic-release`.  

## Commit & PR Conventions  
- Conventional Commits (`feat:`, `fix:`, `chore:`…).  
- PR description template: problem → solution → screenshots (if UI) → follow-ups.  
- Squash-merge to keep history linear.  

## Testing & QA  
- Aim for 90 %+ unit coverage on critical logic (`todoStore`, sync engine).  
- Snapshot-test UI states (completed / active lists).  
- Playwright smoke suite runs in CI; keep it < 2 min.  

## DevOps & CI/CD  
- Docker image built on `main`, tagged (`ghcr.io/...:sha`).  
- Preview deploy via `docker compose up` in CI for E2E run.  
- Keep container ≤ 200 MB final size.  

## Product & Delivery  
- **Ship small, ship often.** Target weekly MVP increments.  
- Log any scope creep straight into the backlog; label **post-MVP**.  
- UI mock-ups show future features—**only implement what PRD marks as MVP**.  

## When You (Copilot) Generate Code or Chat Responses  
- Default to TypeScript; annotate types explicitly.  
- Suggest accessible markup (semantic HTML, `aria-*`).  
- Provide concise explanations—avoid boilerplate unless requested.  
- Highlight potential performance or security pitfalls inline.  

*End of instructions*
