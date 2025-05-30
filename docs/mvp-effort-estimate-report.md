# Todoee MVP Work-Breakdown & Effort-Estimate Report

A structured work-breakdown of every open GitHub issue mapped to the MVP Product-Requirements Document (PRD), with engineering-hour **and story-point** estimates, contingency allowance, and an aggregate timeline to inform scope, resourcing, and schedule decisions.

**Resourcing assumption:** Estimates are based on one staff-level engineer working solo; estimates may shrink if work streams can run in parallel or if additional engineers join the effort.

## Breakdown

| Seq | #  | GitHub Issue                         | Type      | Est. hrs | **SP** |
| --- | -- | ------------------------------------ | --------- | -------- | ----- |
| 1   | 1  | Set-up local dev environment         | Dev-Ops   | **2**    | **3** |
| 2   | 2  | Initial automated PR checks          | Dev-Ops   | **1**    | **2** |
| 3   | 3  | Storybook build & tests in CI        | Dev-Ops   | **1**    | **2** |
| 4  | 24 | Build *taskStore*                    | Front-end | **1**    | **2** |
| 5  | 22 | Build *viewStore*                    | Front-end | **1**    | **2** |
| 6  | 21 | Build *taskEditorStore*              | Front-end | **1**    | **2** |
| 7   | 10 | Build **Tasks View** layout          | Front-end | **1**    | **2** |
| 8   | 6  | Build **Sidebar**                    | Front-end | **2**    | **3** |
| 9   | 7  | Build **Tasks View Header**          | Front-end | **1**    | **2** |
| 10  | 8  | Build **Task Item** component        | Front-end | **1.5**  | **3** |
| 11  | 20 | “Edit task” button on item           | Front-end | **0.5**  | **1** |
| 12  | 13 | Completed-tasks title in header      | Front-end | **0.5**  | **1** |
| 13  | 19 | “Create task” button in header       | Front-end | **0.5**  | **1** |
| 14  | 12 | Sidebar link – completed tasks       | Front-end | **0.5**  | **1** |
| 15  | 17 | Design Task Editor UI                | UX        | **2.5**  | **5** |
| 16  | 18 | Build **Task Editor** component      | Front-end | **2**    | **3** |
| 17  | 4  | PR check – build production app      | Dev-Ops   | **1**    | **2** |
| 18  | 28 | Add E2E tests to PR checks           | Dev-Ops   | **1**    | **2** |
| 19  | 27 | E2E test – view remaining tasks      | QA        | **0.5**  | **1** |
| 20  | 26 | E2E test – view completed tasks      | QA        | **0.5**  | **1** |
| 21  | 25 | E2E test – full CRUD flow            | QA        | **1.5**  | **3** |
| 22  | 30 | Automated deployment to GitHub Pages | Dev-Ops   | **1**    | **2** |
| 23  | 29 | Document application in README       | Docs      | **1**    | **2** |
| 24  | 31 | Create release of version 1          | Dev-Ops   | **1**    | **2** |
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
