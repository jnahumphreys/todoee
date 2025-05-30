# Todoee MVP Work-Breakdown & Effort-Estimate Report

*A structured work-breakdown of every open GitHub issue mapped to the MVP Product-Requirements Document (PRD), with engineering time estimates, contingency allowance, and an aggregate timeline to inform scope, resourcing, and schedule decisions.*

**Resourcing assumption:** Estimates are based on one staff‑level engineer working solo. Durations may shrink if work streams can run in parallel or if additional engineers join the effort.

| Seq |  GitHub Issue No. | GitHub Issue | Type | Est. hrs |
|---|---|---|---|---|
| 1 | 1 | Set-up local dev environment | Dev-Ops | **2** |
| 2 | 2 | Initial automated PR checks | Dev-Ops | **1** |
| 3 | 3 | Storybook build & tests in CI | Dev-Ops | **2** |
| 4 | 5 | PR check – build production app | Dev-Ops | **1.5** |
| 5 | 30 | Automated deployment to GitHub Pages | Dev-Ops | **3** |
| 6 | 18 | Design Task Editor UI | UX | **2** |
| 7 | 7 | Build **Sidebar** | Front-end | **3** |
| 8 | 11 | Build **Tasks View** layout | Front-end | **2** |
| 9 | 8 | Build **Tasks View Header** | Front-end | **1.5** |
| 10 | 14 | Completed-tasks title in header | Front-end | **0.5** |
| 11 | 20 | “Create task” button in header | Front-end | **0.5** |
| 12 | 10 | Build **Task List** component | Front-end | **2** |
| 13 | 9 | Build **Task Item** component | Front-end | **1.5** |
| 14 | 21 | “Edit task” button on item | Front-end | **0.5** |
| 15 | 24 | Build *taskStore* (Zustand) | Front-end | **1.5** |
| 16 | 23 | Build *viewStore* | Front-end | **1** |
| 17 | 22 | Build *taskEditorStore* | Front-end | **1** |
| 18 | 19 | Build **Task Editor** component | Front-end | **3** |
| 19 | 13 | Sidebar link – completed tasks | Front-end | **0.5** |
| 20 | 28 | Add E2E tests to PR checks | Dev-Ops | **2** |
| 21 | 27 | E2E test – view remaining tasks | QA | **1** |
| 22 | 26 | E2E test – view completed tasks | QA | **1** |
| 23 | 25 | E2E test – full CRUD flow | QA | **2** |
| 24 | 29 | Document application in README | Docs | **1.5** |
| 25 | 31 | Create release of version 1 | Dev-Ops | **1** |
|   |   | **Subtotal** |   | **38.5 h** |
|   |   | **Contingency (+15 %)** |   | **+6 h** |
|   |   | **Projected total** | — | **≈ 45 h** |

### Phase snapshot

| Phase | Major activities | Approx. calendar time\* |
|-------|------------------|-------------------------|
| Environment & CI | Seq 1-5 | 2-3 days |
| Core UI scaffolding | Seq 6-14 | 3-4 days |
| State & features | Seq 15-19 | 2-3 days |
| Testing, docs, release | Seq 20-25 | 2 days |
| **Total** |   | **~9-11 working days** |

\*Assumes ~5 focused hours/day.
