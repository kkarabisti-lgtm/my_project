# RevenueGuard AI

> **An agentic revenue-recovery system that turns payment risk into bounded, measurable recovery actions.**

[![CI](https://github.com/kkarabisti-lgtm/my_project/actions/workflows/ci.yml/badge.svg)](https://github.com/kkarabisti-lgtm/my_project/actions/workflows/ci.yml)

**Detect → Diagnose → Decide → Policy Check → Execute → Verify → Learn**

RevenueGuard AI is a portfolio-grade implementation of an autonomous revenue recovery workflow. Instead of stopping at dashboards or AI-generated recommendations, the system models the complete loop: identify revenue at risk, determine a root cause, select a recovery strategy, enforce deterministic policies, execute a bounded action, verify the outcome, measure incremental revenue recovered, and preserve an audit trail.

## Why this project matters

A weak revenue-recovery system says **"this payment may fail."**

RevenueGuard asks a harder engineering question:

> **"What intervention should happen, is it allowed, did it work, and how much incremental revenue did it recover?"**

The design deliberately separates probabilistic AI reasoning from deterministic financial controls. This makes the agent easier to test, constrain, audit, and explain.

## Product architecture

```text
Payment / Checkout / Subscription / Receivable Events
                         ↓
                 Event Ingestion
                         ↓
                Risk & Revenue-at-Risk
                         ↓
                  Root Cause Analysis
                         ↓
                AI Decision / Strategy
                         ↓
              Deterministic Policy Gate
                    ↙           ↘
             Allowed            Block / Review
                ↓
         Bounded Recovery Action
                ↓
          Payment Verification
                ↓
     Incremental Revenue Measurement
                ↓
          Audit Trail + Learning
```

### AI vs. deterministic controls

| Responsibility | Approach |
|---|---|
| Root-cause reasoning | AI-assisted |
| Recovery strategy selection | AI-assisted |
| Message generation | AI-assisted |
| Financial calculations | Deterministic code |
| Retry limits | Deterministic policy |
| Stopping rules | Deterministic policy |
| Compliance / authorization | Deterministic policy |
| Recovery attribution | Verification + deterministic measurement |
| Audit record | Application-controlled |

**Principle:** *AI proposes · policies decide · systems execute · humans supervise.*

## Core capabilities

- **Revenue at Risk** — identify degradation and prioritize exposed revenue.
- **Recovery Cases** — inspect diagnosis, recommended action, policy outcome, execution and verification.
- **Payment recovery** — model recovery workflows for failed payments.
- **Checkout recovery** — identify abandonment and trigger bounded follow-up strategies.
- **Subscription recovery** — support failed-subscription recovery and retry sequencing.
- **B2B receivables** — track overdue receivables and promise-to-pay outcomes.
- **Copilot** — natural-language analytics over recovery data.
- **Strategy Lab** — compare Random, Rule-Based and AI-agent strategies.
- **Audit Log** — retain traceability from event to decision to outcome.

## Engineering highlights

- Agentic workflow with explicit decision boundaries
- Deterministic policy gate between AI reasoning and execution
- Bounded retries and stopping conditions
- Outcome verification before revenue attribution
- Case-level auditability
- Real-time event support through Socket.io
- Analytics and recovery funnel visualization
- Prisma data layer with SQLite for local development and PostgreSQL-ready architecture
- TypeScript/Next.js application with modern React patterns
- CI workflow for lint, Prisma generation and production build checks

## Tech stack

**Frontend / App:** Next.js 16, React 19, TypeScript, Tailwind CSS 4, shadcn/ui

**Data:** Prisma 6, SQLite, PostgreSQL-ready architecture

**AI / Voice:** `z-ai-web-dev-sdk` for LLM, ASR and TTS capabilities

**State / Data:** Zustand, TanStack Query

**Realtime / Analytics:** Socket.io, Recharts

**Validation / UI:** Zod, React Hook Form, Radix UI, Framer Motion

## Repository structure

```text
app/                 Next.js routes and application UI
components/          Reusable interface components
lib/                 Business logic, data access and utilities
prisma/              Database schema and seed data
scripts/             Development / seed scripts
docs/                Architecture and engineering documentation
.github/workflows/   Continuous integration
```

## Run locally

### Requirements

- Bun
- Node.js-compatible environment
- A local SQLite database

### Setup

```bash
bun install
bun run db:push
bun run scripts/seed.ts
bun run dev
```

Create `.env.local` from `.env.example`:

```env
DATABASE_URL="file:./db/custom.db"
```

Then open the local development server at `http://localhost:3000`.

> **Security:** never commit `.env`, API keys, credentials, customer data, or production database files.

## Demo walkthrough

1. Start on **Overview** and inspect the recovery funnel.
2. Open **Revenue at Risk** to identify exposed revenue.
3. Trigger or inspect a **Recovery Case**.
4. Review the AI diagnosis and proposed strategy.
5. Inspect the deterministic **Policy Check**.
6. Execute the bounded recovery workflow.
7. Verify the payment outcome.
8. Inspect recovered-revenue attribution and the **Audit Log**.
9. Use **Strategy Lab** to compare recovery approaches.

## Architecture documentation

See [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) for the system boundaries, reliability principles, and design rationale.

## What I would measure in production

The portfolio implementation is designed around measurable outcomes rather than model activity. Production evaluation should track:

- Incremental revenue recovered
- Recovery rate by failure / risk category
- False-positive recovery attempts
- Cost per recovered unit of revenue
- Recovery latency
- Policy-block rate
- Human-escalation rate
- Duplicate-action / idempotency failures
- Strategy performance versus a human or rule-based baseline

## Responsible automation

Revenue recovery can affect customers and money, so the system is intentionally constrained:

- AI output is not financial authorization.
- Policies can block an AI recommendation.
- High-risk or ambiguous cases can require human review.
- Retry counts and stopping rules are bounded.
- Recovery is counted only after outcome verification.
- Audit records make decisions inspectable.

## Author

**Keerthana Karabisti** — AI Developer

- GitHub: [@kkarabisti-lgtm](https://github.com/kkarabisti-lgtm)
- LinkedIn: [Keerthana Karabisti](https://www.linkedin.com/in/keerthana-karabisti-64799a426/)

---

### Built to demonstrate

**AI engineering · agentic workflows · full-stack development · deterministic financial controls · data modeling · product thinking · observability · responsible automation**
