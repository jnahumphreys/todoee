# **Product Requirements Document (PRD) for MVP: Todoee**

## 1. Purpose
Todoee is a self-hosted task management application designed for individuals, technical professionals or enthusiasts who prefer local-first tools and want full control over their data. Todoee will be distributed as a self-contained Docker image and focus on core task management features without reliance on third-party cloud services.

## 2. Background
Many task management tools today are cloud-based, which introduces concerns around data privacy, vendor lock-in, and platform limitations. Todoee addresses this gap by offering a simple, local-first, and self-hosted task tracker. The MVP aims to deliver essential functionality that allows users to manage tasks independently on their own infrastructure.

## 3. Goals
Deliver a functional, minimalist task tracker with full CRUD capabilities, local persistence, and basic usability features, deployable via Docker.

## 4. Non-Goals
- No collaboration or multi-user features
- No backend or cloud sync
- No mobile-first optimizations
- No user authentication or role management
- No drag-and-drop, filtering, or tagging in MVP

## 5. Assumptions
- Users are comfortable with Docker and self-hosting tools
- Users prefer simplicity and data ownership over advanced features
- MVP will be deployed and tested in modern desktop browsers

## 6. Requirements

### Functional Requirements (MVP)
1. **View Remaining Tasks**  
   Display a list of all remaining tasks, in a separate view.

2. **View Completed Tasks**  
   Display a list of completed tasks, in a separate view.

3. **Create Task**  
   Allow users to add a new task with a title and optional description; the task should be automatically time-stamped on creation.

4. **Edit Task**  
   Allow users to modify an existing task's title and description.

5. **Delete Task**  
   Permanently remove a task from the list.

6. **Report an Issue**  
   Provide a link or interface to open a GitHub issue.

7. **Application Version Display**  
   Show current version number in the UI.

8. **README for Self-Hosting**  
   Include clear instructions for setting up and running the app via Docker.

### Technical Requirements
- Application must adhere to **Semantic Versioning**
- Application must use **React + Zustand** for state management
- Application must persist data using **LocalStorage**
- Application must be built with **Vite**, **TypeScript**, **Tailwind CSS**, and **Headless UI**
- All dependencies and setup should be Dockerized in a single container using **VSCode DevContainers**
- Application should be unit and end-to-end tested to ensure functionality of core functional requirements
- Use **Storybook** for component development
- Use **Prettier**, **ESLint**, and **Husky** for code quality and formatting

## 7. Success Criteria
- Users can perform all task CRUD operations without errors
- Application works across major desktop browsers
- Project README allows a technical user to self-host the app via Docker within 10 minutes
- Local storage accurately reflects task changes after refresh

## 8. Future Considerations
Post-MVP roadmap includes:
- Task search, sorting, and ordering
- Task lists and tagging
- Scheduled tasks and reminders
- Mobile UI enhancements
- PWA/offline support
- Server-side persistence
- Task comments and collaboration
- Drag-and-drop UI features
- Bulk editing of tasks
