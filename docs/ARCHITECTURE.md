# 🧱 Todoee Architecture

**Last updated:** 16-07-2025  
**Purpose:** This document outlines the technical architecture of the Todoee application, a local-first, self-hosted task manager.

---

## 🎯 Goals

- Local-first with full offline support (PWA)
- Real-time sync across devices (e.g. iPad, desktop, phone)
- Minimal dependencies, long-term maintainability
- Deployable as a single Docker container
- Target users are technical individuals who self-host tools

---

## 🏗️ Frontend

| Layer               | Choice                        | Notes |
|---------------------|-------------------------------|-------|
| Framework           | React + TypeScript            | Component-driven architecture (presentation/container split) |
| State Management    | Zustand                       | Global state store; performant and lean |
| UI Library          | Flowbite (Tailwind CSS)       | Minimalist, consistent UI |
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

## 📦 Packaging & Deployment

| Area           | Tooling                  |
|----------------|--------------------------|
| Project Layout | Monorepo (frontend + backend) |
| Build System   | Vite                     |
| CI/CD          | GitHub Actions           |
| Containerization| Docker                  |
| PWA Manifest   | via `vite-plugin-pwa`    |
| Versioning     | `semantic-release` (optional) |
| E2E Testing    | Playwright or Cypress    |
| Component Tests| Storybook Test Runner    |
| DB Seeding     | Prisma `seed.ts` script  |

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
| 1     | Local-only PWA using Zustand + Dexie   |
| 2     | Add backend (Fastify + SQLite) and REST API |
| 3     | *Skip background polling*              |
| 4     | Add WebSockets for real-time sync      |
| 5     | Add offline queue + reconnect sync     |
| 6     | Last-write-wins conflict resolution    |
| 7     | (Post-MVP) Optional merge UX or CRDT for note fields |

---

## 🔖 Key Design Principles

- **Single Source of Truth:** SQLite on backend
- **IndexedDB:** Offline shadow DB and sync queue
- **WebSocket Protocol:** Handles real-time updates and reconnect flush
- **Optimistic Updates:** Immediate UI feedback, reconciled on sync
- **Lean Dependencies:** Avoid unnecessary libraries or frameworks
