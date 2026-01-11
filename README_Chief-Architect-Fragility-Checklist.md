# The Chief Architect’s Fragility Checklist

Use this checklist to identify architectural fragility early and address it systematically.
Fragility is a signal that systems cannot safely absorb change.

> **Definition:** A system is fragile when small changes cause disproportionate failures.

---

## Fragility Checklist (Chief Architect View)

| Dimension | Fragility Signal | What It Looks Like in Practice | Resilient Architecture Pattern |
|---------|----------------|--------------------------------|--------------------------------|
| Change Safety | Fear of deployments | Large, risky releases, rollback anxiety, late-night hotfixes | Small, reversible changes with fast, reliable rollback |
| Coupling | Hidden dependencies | Unplanned breakages, surprise downstream impact | Explicit APIs, event contracts, clear ownership boundaries |
| Observability | Guesswork during incidents | War rooms, log hunting, unclear root cause | Standard logs, metrics, traces with clear correlation |
| Knowledge Distribution | Hero engineers | Progress depends on a few individuals | Simplicity, shared ownership, platform-encoded knowledge |
| Operational Readiness | Designed only for happy paths | On-call pain, frequent escalations, burnout | Failure-aware design, SLOs, error budgets |
| Governance & Consistency | Repeated architecture debates | Inconsistent implementations across teams | Golden paths with automated guardrails |
| Technical Debt | Deferred fixes with no plan | Workarounds become permanent | Intentional debt tracking and scheduled payoff |
| Scalability | Assumptions break at scale | Performance collapses under load | Horizontal scalability and capacity planning |
| Security & Compliance | Controls applied late | Audit surprises, emergency fixes | Security-by-default and policy-as-code |
| AI & Automation Readiness | Uncontrolled autonomy | AI decisions without traceability | Explainable, auditable systems with human override |

---

## How to Use This Table

- Use during architecture reviews and retrospectives
- Identify high-risk fragility hotspots
- Prioritize platform and golden path investments
- Track improvement over time

---

## Chief Architect Reminder

> **Fragility is not a team failure — it is an architectural signal.**
