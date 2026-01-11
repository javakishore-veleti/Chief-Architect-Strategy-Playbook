# Fragile vs Resilient Systems (One Graphic)

This one-page graphic is designed for architecture reviews. It contrasts how *fragile* and *resilient* systems behave across key dimensions.

> **Definition:** A system is **fragile** when small changes cause disproportionate failures.  
> A system is **resilient** when it absorbs change and failure while maintaining predictable behavior.

---

## One Graphic: Fragile vs Resilient

```
                         ┌───────────────────────────────────────────────────┐
                         │              CHANGE + FAILURE PRESSURE            │
                         │     (releases, traffic spikes, outages, audits)   │
                         └───────────────────────────────────────────────────┘
                                           │
                                           │
                   ┌───────────────────────┴───────────────────────┐
                   │                                               │
                   v                                               v
      ┌──────────────────────────────┐               ┌──────────────────────────────┐
      │         FRAGILE SYSTEM        │               │        RESILIENT SYSTEM      │
      ├──────────────────────────────┤               ├──────────────────────────────┤
      │ Small changes ripple widely  │               │ Small changes are contained   │
      │ Hidden dependencies exist    │               │ Dependencies are explicit     │
      │ Observability is weak        │               │ Observability is built-in     │
      │ Deployments feel risky       │               │ Deployments are routine       │
      │ Rollback is slow/uncertain   │               │ Rollback is fast & reliable   │
      │ Ops relies on heroics        │               │ Ops is predictable & calm     │
      │ Security is added late       │               │ Security is default-by-design │
      │ Knowledge is siloed          │               │ Knowledge is distributed      │
      └──────────────────────────────┘               └──────────────────────────────┘
                   │                                               │
                   │                                               │
                   v                                               v
      ┌──────────────────────────────┐               ┌──────────────────────────────┐
      │           OUTCOMES            │               │            OUTCOMES           │
      ├──────────────────────────────┤               ├──────────────────────────────┤
      │ Fear of change               │               │ Confidence to change          │
      │ Longer incidents (high MTTR) │               │ Faster recovery (low MTTR)    │
      │ Slower delivery over time    │               │ Faster delivery over time     │
      │ Higher audit/regulatory risk │               │ Lower audit/regulatory risk   │
      └──────────────────────────────┘               └──────────────────────────────┘
```

---

## Quick Comparison Table (Optional)

| Dimension | Fragile | Resilient |
|---|---|---|
| Change impact | Ripple effects | Contained blast radius |
| Dependencies | Hidden | Explicit contracts |
| Deployments | Risky events | Routine |
| Rollback | Slow/uncertain | Fast/reliable |
| Observability | Weak | Built-in |
| Operations | Hero-driven | Predictable |
| Security | Added late | Default-by-design |
| Knowledge | Siloed | Distributed |

---

## Chief Architect Note

> **Fragility is an architectural signal.**  
> Golden paths, platform defaults, and automated guardrails are the most scalable way to shift from fragile to resilient.
