# 🧱 Todoee Architecture

**Last updated:** 17-07-2025  
**Purpose:** This document outlines the technical architecture of the Todoee application, a local-first, self-hosted task manager.

---

## 🎯 Goals

- Local-first with full offline support (PWA)
- Real-time sync across devices (e.g. iPad, desktop, phone)
- Minimal dependencies, long-term maintainability
- Deployable as a single Docker container
- Component-driven development with Storybook
- Isolated development environment with VSCode dev containers
- Target users are technical individuals who self-host tools

---

## 🏗️ Frontend

| Layer               | Choice                        | Notes |
|---------------------|-------------------------------|-------|
| Framework           | React + TypeScript            | Component-driven architecture with co-located stories |
| State Management    | Zustand                       | Global state store; performant and lean |
| UI Library          | Flowbite (Tailwind CSS)       | Minimalist, consistent UI |
| Component Development| Storybook                    | Component-driven development, stories as tests |
| Visual Testing      | Chromatic                     | Automated visual regression testing |
| Persistence         | IndexedDB (via Dexie.js)      | Local persistence and offline queueing |
| Routing             | None                          | View toggles handled via state, no URL routing |
| PWA Support         | `vite-plugin-pwa`             | Installable, offline-capable |
| Optimistic UI       | Yes                           | Immediate updates in UI before backend confirmation |
| Sync Logic          | WebSockets + IndexedDB        | Queue writes offline, sync on reconnect, broadcast updates live |

---

## 🔧 Backend

| Layer            | Choice               | Notes |
|------------------|----------------------|-------|
| Runtime          | Node.js              | Runs within Docker container |
| Framework        | Fastify              | Fast, TS-native, extensible |
| WebSocket Support| `@fastify/websocket` | Native WebSocket handling |
| Database         | SQLite               | File-based DB; ideal for Docker and single-user setup |
| ORM              | Prisma               | Type-safe DB access, migrations, seeding |
| API Style        | REST + WebSockets    | REST for initial loads, WebSocket for live sync |
| Conflict Strategy| Last-write-wins      | Uses `updatedAt` timestamp per task |

---

## 🏢 Project Structure

### **Monorepo Layout**

```
todoee/
├── .devcontainer/           # VSCode dev container configuration
├── .github/workflows/       # CI/CD automation
├── .storybook/             # Global Storybook configuration
├── apps/
│   ├── frontend/           # React PWA application
│   │   └── src/
│   │       ├── components/ # React components (with co-located stories)
│   │       ├── stores/     # Zustand state management
│   │       ├── services/   # API/sync services
│   │       └── hooks/      # Custom React hooks
│   └── backend/            # Fastify API server
│       ├── src/           
│       │   ├── routes/     # API route handlers
│       │   ├── services/   # Business logic
│       │   └── websocket/  # Real-time sync handlers
│       └── prisma/         # Database schema & migrations
├── packages/
│   └── shared-types/       # Shared TypeScript contracts
├── tools/
│   ├── docker/            # Production deployment
│   └── scripts/           # Build automation
└── tests/
    ├── e2e/              # End-to-end testing (Playwright)
    └── integration/      # API integration tests
```

### **Component Organization**

Components follow a co-located pattern with stories and tests:

```
components/
├── ui/                    # Base UI components
│   ├── Button/
│   │   ├── Button.tsx
│   │   ├── Button.stories.tsx
│   │   └── Button.test.ts
│   └── Input/
├── features/              # Feature-specific components
│   └── tasks/
│       ├── TaskList/
│       ├── TaskItem/
│       └── TaskForm/
└── layout/               # Layout components
```

---

## 🔄 Data Flow / Sync Model

### ✅ Initial App Load
- Use `fetch` to load tasks from REST API.
- Hydrate Zustand and IndexedDB from server response.

### ✅ Real-Time Edits (Online)
- Use WebSocket to send task updates.
- Backend saves to SQLite and broadcasts to other devices.

### ✅ Offline Edits
- Updates saved to IndexedDB and queued.
- On reconnect, send queued changes via WebSocket.
- Backend saves changes and broadcasts updates.

### ✅ Optional Full Re-Sync
- Can optionally `fetch` all tasks to ensure consistency after long disconnection.

---

## 🛠️ Development Environment

### **Dev Container Strategy**

| Aspect              | Choice                    | Rationale |
|---------------------|---------------------------|-----------|
| Container Setup     | Single dev container      | Simplified management, shared Node.js tooling |
| Database            | SQLite with named volume   | Development persistence, production parity |
| Port Management     | 3000 (frontend), 3001 (backend), 6006 (Storybook) | Clear service separation |
| VSCode Integration  | Unified workspace         | Full-stack debugging, shared extensions |

### **Component Development Workflow**

1. **Design:** Create components in isolation using Storybook
2. **Document:** Write stories that serve as documentation
3. **Test:** Stories function as component tests via Storybook test runner
4. **Visual QA:** Chromatic provides automated visual regression testing
5. **Integration:** Compose components into features and pages

---

## 📦 Build & Deployment

### **Development**

| Tool                | Purpose                          |
|---------------------|----------------------------------|
| VSCode Dev Container| Isolated, reproducible dev environment |
| Storybook          | Component development and testing |
| Vite               | Fast frontend development server |
| TypeScript         | Type safety across monorepo     |
| Workspace Commands | Unified scripts across apps     |

### **Testing Strategy**

| Layer              | Tooling                    | Coverage |
|--------------------|----------------------------|----------|
| Component Tests    | Storybook Test Runner      | UI components in isolation |
| Visual Tests       | Chromatic                  | Visual regression detection |
| Integration Tests  | Custom test suite          | API endpoints and data flow |
| E2E Tests          | Playwright                 | Complete user workflows |

### **Production Deployment**

| Area               | Tooling                    |
|--------------------|----------------------------|
| Containerization   | Docker (multi-stage build) |
| CI/CD              | GitHub Actions             |
| Database           | SQLite with volume mounts  |
| Static Assets      | Nginx (within container)   |
| Monitoring         | Docker health checks       |

---

## 🔗 Tooling Links

Below are links to the primary tooling used in Todoee's architecture:

- **React**: [https://reactjs.org/](https://reactjs.org/)
- **TypeScript**: [https://www.typescriptlang.org/](https://www.typescriptlang.org/)
- **Zustand**: [https://github.com/pmndrs/zustand](https://github.com/pmndrs/zustand)
- **Flowbite**: [https://flowbite.com/](https://flowbite.com/)
- **Storybook**: [https://storybook.js.org/](https://storybook.js.org/)
- **Chromatic**: [https://www.chromatic.com/](https://www.chromatic.com/)
- **Dexie.js**: [https://dexie.org/](https://dexie.org/)
- **Fastify**: [https://www.fastify.io/](https://www.fastify.io/)
- **SQLite**: [https://sqlite.org/](https://sqlite.org/)
- **Prisma**: [https://www.prisma.io/](https://www.prisma.io/)
- **Docker**: [https://www.docker.com/](https://www.docker.com/)
- **Vite**: [https://vitejs.dev/](https://vitejs.dev/)
- **Playwright**: [https://playwright.dev/](https://playwright.dev/)
- **GitHub Actions**: [https://github.com/features/actions](https://github.com/features/actions)

---

## ❌ Deliberately Out of Scope for MVP

- No authentication or user roles
- No collaborative multi-user editing
- No cloud sync or hosted backend
- No tags, filters, or complex search
- No CRDT or merge conflict UI
- No mobile-first design (desktop-first)

---

## 🪜 Phased Rollout Plan

| Phase | Feature Set                            |
|-------|----------------------------------------|
| 1     | Component library in Storybook        |
| 2     | Local-only PWA using Zustand + Dexie   |
| 3     | Add backend (Fastify + SQLite) and REST API |
| 4     | *Skip background polling*              |
| 5     | Add WebSockets for real-time sync      |
| 6     | Add offline queue + reconnect sync     |
| 7     | Last-write-wins conflict resolution    |
| 8     | (Post-MVP) Optional merge UX or CRDT for note fields |

---

## 🔖 Key Design Principles

- **Component-First:** Build UI components in isolation before integration
- **Stories as Tests:** Storybook stories serve as both documentation and tests
- **Single Source of Truth:** SQLite on backend
- **IndexedDB:** Offline shadow DB and sync queue
- **WebSocket Protocol:** Handles real-time updates and reconnect flush
- **Optimistic Updates:** Immediate UI feedback, reconciled on sync
- **Lean Dependencies:** Avoid unnecessary libraries or frameworks
- **Developer Experience:** Isolated environments, easy onboarding, fast feedback loops