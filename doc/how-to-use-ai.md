# How to Use SaaS AI Factory (.ai)

Welcome to the **SaaS AI Factory**! This workspace uses an autonomous, multi-stack development pipeline that takes your Product Requirements Document (PRD), conducts an interactive Q&A discovery, scaffolds your custom setup, and automatically builds, tests, and validates your SaaS application.

Because the system is driven by cooperating AI agents, **you do not need to run local setup steps manually.** The AI agents act as the strategic planners and software engineers.

---

## 🚀 The Getting Started Workflow (For Fresh Users)

Follow these simple steps to build your SaaS application from scratch.

### Step 1: Complete your PRD Document
Open the Product Requirements Document template and fill in your app requirements:
👉 **[doc/prd.md](../doc/prd.md)**

*Describe the features, target users, and key screens. Be as specific as possible — the quality of your PRD determines the quality of the generated code.*

### Step 2: Trigger Ingestion & Discovery
Message the AI agent in the chat to launch the workflow:
> *"I have completed my PRD. Please ingest doc/prd.md and start code generation."*

---

## 💬 The Interactive Q&A Discovery Phase (Automatic)

Once triggered, the AI agent will analyze your PRD and ask you a few quick questions in the chat to define your custom technology stack:

1. **Project structure**: Do you want a **Shared Monorepo** (with a `shared` types package) or **Decoupled Standalone Projects** (if you plan to deploy backend and frontend on completely different servers)?
2. **Deploy infrastructure**: **Docker Compose** containers vs. **Manual / PaaS deployments** (like Vercel and Render).
3. **Database**: **MongoDB** (NoSQL via Mongoose) or **Postgres / MySQL** (SQL via Prisma ORM).
4. **Caching**: **Redis** (required for queues) vs. **Local In-Memory Cache**.
5. **Multi-Tenancy**: A **Multi-tenant SaaS** (with RBAC) vs. a **Single-Client** application.
6. **Integrations** (Payments, Logs, Real-Time): These are **optional and skippable**. The AI will only ask about them if it detects them in your PRD.

---

## 🛠️ Behind the Scenes (Autonomous Pipeline)

Once you answer the questionnaire, the cooperating agents execute the pipeline:

```
┌─────────────────────────────────┐
│       1. PRD Ingestion          │
│  Super Agent reads and checks   │
│  doc/prd.md for completeness.   │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│      2. Discovery Q&A           │
│  Super Agent asks custom stack  │
│  questions based on the PRD.    │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│     3. Custom Scaffolding       │
│  CLI script setups directory,   │
│  package.json, and DB ORMs.     │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│       4. Phased Planning        │
│  Designs database schemas, APIs,│
│  architecture, & phase tasks.   │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│     5. Phase Execution          │
│  Backend and Frontend agents    │
│  write the code phase-by-phase. │
└────────────────┬────────────────┘
                 │
                 ▼
┌─────────────────────────────────┐
│      6. QA, Review, & Linter    │
│  Runs test suites and linter    │
│  to enforce strict architecture.│
└─────────────────────────────────┘
```

---

## 📊 Monitoring Progress & Logs

You can watch the build progress and review logs by inspecting the status files in the **`.ai/project-management/`** directory. All updates are auto-synced by our CLI, saving token costs:

* **[project-status.md](../.ai/project-management/project-status.md)**: Check the high-level project status (Awaiting PRD, Planning, In Progress, Blocked, Completed).
* **[progress.md](../.ai/project-management/progress.md)**: Track the active task list showing progress bar, completed task count, and agent assignments.
* **[roadmap.md](../.ai/project-management/roadmap.md)**: View the generated technical plan and structured phase checklist.
* **[current-phase.md](../.ai/project-management/current-phase.md)**: View the active phase's details, tasks, and completion criteria.

---

## ⚙️ Developer CLI Commands

If you ever need to inspect or run checks yourself, you can run these commands from the root directory:

* **Codebase Linter Check**:
  ```bash
  node .ai/scripts/validate-project.js
  ```
  *(Checks naming conventions, file size limits, and repository pattern rules).*

* **Database/Cache Scaffolder**:
  ```bash
  node .ai/scripts/scaffold-starter.js
  ```
  *(Generates the directory skeleton based on configuration).*

* **Sync Status Logs manually**:
  ```bash
  node .ai/scripts/status-manager.js sync
  ```
  *(Synchronizes the JSON database state to the markdown logs).*
