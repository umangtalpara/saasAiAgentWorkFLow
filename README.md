# SaaS AI Factory

Welcome to the **SaaS AI Factory**! This repository is designed as an autonomous, multi-agent software development environment. It utilizes cooperative AI agents to process Product Requirements Documents (PRDs) and automatically generate, test, review, and prepare code for a complete SaaS application.

## Repository Structure

The repository is structured as follows:

```
saasAiAgentWorkFLow/
├── AGENTS.md            ← Shared spine containing core rules & directory references
├── CLAUDE.md            ← Claude Code adapter directing to AGENTS.md
├── GEMINI.md            ← Google Antigravity adapter directing to AGENTS.md
├── README.md            ← This human entry point
│
├── .ai/                 ← Canonical store of AI Agent rules and context
│   ├── settings.json    ← Global tech stack and directory configurations
│   ├── context/         ← Development, naming, architecture, and UI rules
│   ├── skills/          ← Technical capabilities for specific agent domains (.md)
│   ├── agents/          ← Base personas and instructions for each agent (.md)
│   ├── workflows/       ← Step-by-step agent workflow checklists (.md)
│   ├── templates/       ← PRD and Code Review templates (.md)
│   ├── memory/          ← Session log, blocker tracker, and decision log
│   └── project-management/ ← Progress tracker, roadmap, and phase status
│
├── .claude/             ← Claude Code configuration and skill/command stubs
├── .cursor/             ← Cursor rules (.mdc) and command shims
├── .agents/             ← Google Antigravity workspace rules and workflow shims
│
├── doc/                 ← Product Requirements Documents (doc/prd.md)
│
└── codebase/            ← Generated applications
    ├── backend/         ← NestJS 11 backend codebase (standardized on BullMQ + Redis)
    └── frontend/        ← Next.js 14 frontend codebase
```

## How to Get Started

1. Check the **[How-To Guide](doc/how-to-use-ai.md)** for detailed instructions on utilizing the AI Factory workflow.
2. Complete your Product Requirements Document at **[doc/prd.md](doc/prd.md)**.
3. Use your preferred AI coder tool (Claude Code, Cursor, or Google Antigravity) to initiate the development loop. The tool will read rules from the root `AGENTS.md` and thin adapters automatically.
