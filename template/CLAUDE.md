# The Bizz - Claude Instructions

## Overview
This is an AI-powered business organization. The Owner (Ruben) provides direction; the organization executes autonomously.

## Key Commands
- `/discuss` - Strategic conversation with Owner
- `/do` - Autonomous execution mode

## Project Structure
```
the-bizz/
├── ORG.txt              # Organizational charter
├── PRD.txt              # Product requirements
├── STATUS.md            # Org-wide progress (CEO maintains)
├── CHANGELOG.md         # Releases and deployments
├── FINANCES.md          # Budget and cost tracking
├── CLAUDE.md            # This file
├── .claude/
│   ├── skills/
│   │   ├── discuss/     # /discuss skill
│   │   └── do/          # /do skill
│   └── agents/          # Per-agent memory
│       ├── ceo/
│       │   ├── MEMORY.md
│       │   └── TODO.md
│       ├── cto/
│       ├── cpo/
│       ├── cmo/
│       ├── cfo/
│       ├── legal/
│       ├── frontend/
│       ├── backend/
│       ├── devops/
│       ├── qa/
│       ├── security/
│       ├── design/
│       ├── brand/
│       ├── docs/
│       ├── content/
│       └── growth/
├── src/                 # Application source
├── docs/                # Documentation
├── design/              # Design assets
├── legal/               # Contracts, ToS, Privacy Policy
└── infra/               # Infrastructure configs
```

## Working Conventions

### Autonomy
- Execute fully autonomously
- Only escalate critical blockers
- Make reasonable decisions without asking
- Each agent logs decisions in their MEMORY.md

### Tech Stack (Default)
- Frontend: Next.js 14+, TypeScript, Tailwind CSS on Cloudflare Pages
- Edge Logic: Cloudflare Workers
- Backend (when needed): .NET AOT on Fly.io (only if can't run on Workers)
- Database: Cloudflare D1 (primary) or Fly.io PostgreSQL (for .NET backends)
- Auth: Clerk (Google/Apple social login)
- Hosting: Cloudflare (preferred), Fly.io (separate backends only)
- Monitoring: Sentry
- Email: Resend
- Payments: Stripe (when needed)
- CI/CD: GitHub Actions

### Code Standards
- TypeScript everywhere
- Functional components with hooks
- Tailwind for styling (no CSS modules)
- ESLint + Prettier
- Test critical paths

### Git Workflow
- `main` branch is production
- Feature branches for new work
- Squash merge PRs
- Conventional commits

### Deployment
- Push to main triggers deploy
- Preview deployments on PRs
- Zero-downtime deployments

## Agent Memory System
Each agent maintains persistent memory:
- `MEMORY.md` - Key decisions, learnings, preferences
- `TODO.md` - Current and upcoming tasks

When acting as an agent, always:
1. Read your MEMORY.md first
2. Update TODO.md as you work
3. Log important decisions to MEMORY.md
