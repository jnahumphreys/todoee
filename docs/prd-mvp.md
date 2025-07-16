# **Product Requirements Document (PRD) for MVP: Todoee**

## 1. Purpose
Todoee is a self-hosted task management application designed for individuals, technical professionals, or enthusiasts who prefer local-first tools and want full control over their data. Todoee will be distributed as a self-contained Docker image and focus on core task management features without reliance on third-party cloud services.

## 2. Background
Many task management tools today are cloud-based, which introduces concerns around data privacy, vendor lock-in, and platform limitations. Todoee addresses this gap by offering a simple, local-first, and self-hosted task tracker. The MVP aims to deliver essential functionality that allows users to manage tasks independently on their own infrastructure.

## 3. Goals
Deliver a functional, minimalist task tracker with:
- Full CRUD capabilities
- Offline-first experience
- Real-time multi-device sync
- Local and server persistence
- Easy self-hosting via Docker

## 4. Non-Goals
- No collaboration or multi-user features
- No cloud-based backend or SaaS sync service
- No mobile-first optimizations
- No user authentication or role management
- No drag-and-drop, filtering, or tagging in MVP

## 5. Assumptions
- Users are comfortable with Docker and self-hosting tools
- Users value simplicity and data ownership over advanced features
- MVP will be deployed and used primarily in modern desktop browsers
- Users may access the app from multiple devices on the same network (e.g., iPad, desktop, phone)

## 6. Requirements

### Functional Requirements (MVP)
1. **View Remaining Tasks**  
   Display a list of all remaining (incomplete) tasks.

2. **View Completed Tasks**  
   Display a list of completed tasks, in a separate view.

3. **Create Task**  
   Allow users to add a new task with a title and optional description; the task should be automatically time-stamped on creation.

4. **Edit Task**  
   Allow users to modify an existing task's title and description.

5. **Delete Task**  
   Permanently remove a task from the list.

6. **Toggle Task Status**  
   Mark a task as completed or revert it to incomplete.

7. **Report an Issue**  
   Provide a link or interface to open a GitHub issue.

8. **Application Version Display**  
   Show the current version number in the UI.

9. **README for Self-Hosting**  
   Include clear instructions for setting up and running the app via Docker.

### Technical Requirements

For detailed architecture and sync logic, see [`ARCHITECTURE.md`](ARCHITECTURE.md)

## 7. Success Criteria

- Users can perform all task CRUD operations with no errors across supported devices
- Application works across major desktop browsers and supports offline usage
- Real-time updates propagate instantly across open devices on the same network
- Project README enables a technical user to self-host the app via Docker within 10 minutes
- Tasks persist reliably across sessions and reflect changes after app reload
- Offline changes sync automatically and conflict-free upon reconnection

## 8. Future Considerations

Post-MVP roadmap includes:
- Task search, sorting, and ordering
- Task lists and tagging
- Scheduled tasks and reminders
- Mobile UI enhancements
- Conflict resolution UI for simultaneous edits
- User authentication and multiple-user support
- Drag-and-drop task reordering
- Bulk editing of tasks
- File attachments or rich content in task descriptions
