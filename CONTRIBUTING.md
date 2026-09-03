# Contributing

RevenueGuard AI is structured as an engineering portfolio project and an experimentation environment for agentic revenue recovery.

## Development workflow

1. Create a focused branch for your change.
2. Keep financial calculations and policy enforcement deterministic.
3. Add tests for business-critical behavior.
4. Run lint/build checks before opening a pull request.
5. Document meaningful architectural changes.

## Safety rules

- Never commit API keys, database credentials, or production customer data.
- Do not let an LLM directly authorize financial actions.
- Preserve auditability for recovery decisions and outcomes.
- Keep retry and escalation limits explicit.
