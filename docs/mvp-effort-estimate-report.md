# Todoee MVP Work-Breakdown & Effort-Estimate Report

A structured work-breakdown of every open GitHub issue mapped to the MVP Product-Requirements Document (PRD), with engineering-hour **and story-point** estimates, contingency allowance, and an aggregate timeline to inform scope, resourcing, and schedule decisions.

**Resourcing assumption:** Estimates are based on one staff-level engineer working solo; estimates may shrink if work streams can run in parallel or if additional engineers join the effort.

## Breakdown

| Seq | #  | GitHub Issue                         | Type      | Est. hrs | **SP** |
| --- | -- | ------------------------------------ | --------- | -------- | ----- |
| 1   | 1  | Set-up local dev environment         | Dev-Ops   | **2**    | **3** |
| 2   | 2  | Initial automated PR checks          | Dev-Ops   | **1**    | **2** |
| 3   | 3  | Storybook build & tests in CI        | Dev-Ops   | **1**    | **2** |
| 4   | 5  | PR check – build production app      | Dev-Ops   | **1**    | **2** |
| 5   | 30 | Automated deployment to GitHub Pages | Dev-Ops   | **1**    | **2** |
| 6   | 18 | Design Task Editor UI                | UX        | **2.5**  | **5** |
| 7   | 7  | Build **Sidebar**                    | Front-end | **2**    | **3** |
| 8   | 11 | Build **Tasks View** layout          | Front-end | **1**    | **2** |
| 9   | 8  | Build **Tasks View Header**          | Front-end | **1**    | **2** |
| 10  | 14 | Completed-tasks title in header      | Front-end | **0.5**  | **1** |
| 11  | 20 | “Create task” button in header       | Front-end | **0.5**  | **1** |
| 12  | 10 | Build **Task List** component        | Front-end | **1**    | **2** |
| 13  | 9  | Build **Task Item** component        | Front-end | **1.5**  | **3** |
| 14  | 21 | “Edit task” button on item           | Front-end | **0.5**  | **1** |
| 15  | 24 | Build *taskStore* (Zustand)          | Front-end | **1**    | **2** |
| 16  | 23 | Build *viewStore*                    | Front-end | **1**    | **2** |
| 17  | 22 | Build *taskEditorStore*              | Front-end | **1**    | **2** |
| 18  | 19 | Build **Task Editor** component      | Front-end | **2**    | **3** |
| 19  | 13 | Sidebar link – completed tasks       | Front-end | **0.5**  | **1** |
| 20  | 28 | Add E2E tests to PR checks           | Dev-Ops   | **1**    | **2** |
| 21  | 27 | E2E test – view remaining tasks      | QA        | **0.5**  | **1** |
| 22  | 26 | E2E test – view completed tasks      | QA        | **0.5**  | **1** |
| 23  | 25 | E2E test – full CRUD flow            | QA        | **1.5**  | **3** |
| 24  | 29 | Document application in README       | Docs      | **1**    | **2** |
| 25  | 31 | Create release of version 1          | Dev-Ops   | **1**    | **2** |
|     |    | **Subtotal**                         |           | **27.5 h** | **52 SP** |
|     |    | **Contingency (+15 %)**              |           | **+4 h** | *(n/a)* |
|     |    | **Projected total**                  | —         | **≈ 31.5 h** | **≈ 52 SP** |

## Phase snapshot

| Phase                  | Major activities | Approx. calendar time* |
| ---------------------- | ---------------- | ----------------------- |
| Environment & CI       | Seq 1-5          | 1-2 days                |
| Core UI scaffolding    | Seq 6-14         | 2 days                  |
| State & features       | Seq 15-19        | 1 day                   |
| Testing, docs, release | Seq 20-25        | 1 day                   |
| **Total**              |                  | **~5-6 working days**   |

\*Assumes \~5 focused hours/day.
