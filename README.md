# RevenueGuard AI — Autonomous Revenue Recovery Agent

> Detect revenue at risk → Diagnose the cause → Decide the best intervention → Check whether it is allowed → Execute recovery → Verify payment → Measure incremental revenue recovered → Maintain an audit trail.

**Tagline:** Detect → Diagnose → Decide → Recover → Learn

**Product principle:** AI proposes · Policies decide · Systems execute · Humans supervise

## What it is

RevenueGuard AI is an AI revenue-recovery agent designed to recover money that would otherwise be lost through payment failures, checkout abandonment, subscription failures, and overdue receivables.

The north-star metric is **incremental revenue recovered** — actual recovered money compared with a human-only baseline, rather than predictions or alerts.

## Tech stack

- Next.js 16 + TypeScript
- Tailwind CSS 4 + shadcn/ui
- Prisma + SQLite (PostgreSQL-ready architecture)
- z-ai-web-dev-sdk for LLM/ASR/TTS capabilities
- Socket.io for real-time events
- Recharts for analytics
- Zustand + TanStack Query for state/data

## Core workflow

```text
Payment / Webhook Events
        ↓
Event Ingestion
        ↓
Risk Engine
        ↓
Root Cause Analysis
        ↓
AI Decision Engine
        ↓
Deterministic Policy Engine
        ↓
Recovery Workflow
        ↓
Payment Verification
        ↓
Recovery Analytics + Audit Trail
```

**Safety principle:** the LLM handles reasoning, diagnosis, strategy selection, and message generation. Money calculations, policy enforcement, retry limits, stopping rules, and compliance decisions remain deterministic.

## Main views

- Overview — KPIs, recovery funnel, before/after metrics
- Revenue at Risk — degradation and risk breakdowns
- Recovery Cases — diagnosis, recommendation, policy decision, audit timeline
- Payments / Subscriptions / Receivables — operational event tables
- Promise to Pay — kept/broken promise tracking
- Copilot — natural-language data Q&A
- Strategy Lab — Random vs Rule-Based vs AI Agent comparison
- Audit Log — traceable recovery actions

## Demo flow

1. Open Overview and inspect live KPIs.
2. Run a recovery workflow.
3. Open a recovery case and inspect diagnosis + recommendation.
4. Review deterministic policy approval/blocking/human-review rules.
5. Verify recovered revenue and the audit timeline.
6. Compare strategies in Strategy Lab.
7. Inspect the audit log.

## Local setup

```bash
bun install
bun run db:push
bun run scripts/seed.ts
bun run dev
```

Create `.env` locally with:

```env
DATABASE_URL="file:./db/custom.db"
```

Never commit real credentials or secrets.

## Interview focus

RevenueGuard demonstrates an agentic system that goes beyond identifying revenue risk: it chooses bounded interventions, applies non-overridable policies, executes recovery workflows, verifies outcomes, measures incremental recovered revenue, and records an audit trail.

## Author

Keerthana Karabisti
GitHub: https://github.com/kkarabisti-lgtm
