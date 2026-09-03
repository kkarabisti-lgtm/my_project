# RevenueGuard AI — Architecture

## System goal

Recover incremental revenue from payment failures, checkout abandonment, subscription failures, and overdue receivables while keeping financial and compliance decisions deterministic.

## High-level flow

```text
Payment / Webhook Events
        |
        v
Event Ingestion
        |
        v
Risk Scoring + Revenue-at-Risk Detection
        |
        v
Root Cause Analysis
        |
        v
AI Decision / Strategy Selection
        |
        v
Deterministic Policy Gate
   +----+----+
   |         |
Allowed   Human Review / Block
   |
   v
Recovery Action
   |
   v
Payment Verification
   |
   v
Incremental Revenue Measurement
   |
   v
Audit Trail + Learning Signals
```

## Agent boundary

The LLM is used for reasoning-heavy work such as diagnosis, strategy selection, prioritisation, and message generation. It does **not** own financial arithmetic, retry limits, compliance rules, stopping conditions, or final authorization.

Those controls belong to deterministic application code so that the system remains bounded, testable, and auditable.

## Core product surfaces

- **Overview:** recovery KPIs and funnel
- **Revenue at Risk:** risk/degradation analysis
- **Recovery Cases:** case-level diagnosis and action timeline
- **Payments / Subscriptions / Receivables:** operational records
- **Promise to Pay:** promise tracking and follow-up
- **Copilot:** natural-language analytics
- **Strategy Lab:** strategy comparison
- **Audit Log:** traceable actions and outcomes

## Data model direction

The application uses Prisma with SQLite for local development and is structured to support PostgreSQL in production. Financial events, recovery cases, decisions, actions, verification outcomes, and audit records should remain traceable through stable identifiers.

## Reliability principles

1. **Idempotent recovery actions** — the same event must not trigger duplicate money-moving actions.
2. **Bounded retries** — every recovery strategy has explicit retry/stopping limits.
3. **Policy before execution** — AI output is advisory until deterministic policy checks pass.
4. **Human escalation** — ambiguous, high-value, or policy-sensitive cases can be routed for review.
5. **Verification before attribution** — revenue is counted as recovered only after outcome verification.
6. **Auditability** — decisions should retain reason, policy result, action, timestamp, and outcome.

## Local development

```bash
bun install
bun run db:push
bun run scripts/seed.ts
bun run dev
```
