# Risk and Decisions

## Purpose

Use this reference when the project contains consequential unknowns, irreversible actions, cross-team decisions, production risk, security implications, or assumptions that can invalidate downstream work.

## Risk is work when it can invalidate work

Do not maintain a decorative risk register. A risk matters when it changes sequence, packet scope, validation depth, ownership, contingency, or approval.

For each meaningful risk record:

```markdown
- ID: RISK-001
- Condition: what may become true
- Consequence: what fails or becomes more expensive
- Likelihood/confidence: qualitative unless real data supports more precision
- Exposure: packets/deliverables affected
- Mitigation: action that reduces likelihood or consequence
- Trigger: evidence that the risk is materializing
- Owner role: who watches/acts
- Contingency: what happens if triggered
```

Do not fabricate numeric probabilities to make uncertainty look scientific.

## Risk-first sequencing

Move a risk earlier when:
- it can invalidate multiple downstream packets
- the cost of discovering it later is high
- it depends on an external party with uncertain lead time
- it affects architecture, data safety, security, compliance, or production recovery

Convert the uncertainty into a bounded discovery packet when direct evidence can materially reduce it.

## Assumptions

Record assumptions that downstream work relies on.

An assumption should have:
- statement
- reason it is currently believed
- affected packets
- validation owner/method
- deadline by which it must become a fact

Promote an assumption to a verified fact when evidence exists. Mark it invalidated when evidence contradicts it and re-evaluate dependent packets.

Do not allow "we assumed" to become hidden architecture.

## Decisions

Record decisions when they constrain future work, especially:
- architectural boundaries
- public interfaces/contracts
- data models/migrations
- security policy
- technology/vendor choices
- operational/recovery strategy
- scope or acceptance changes

A lightweight decision record:

```markdown
# DEC-001 — <decision>

## Context
What forced the decision now?

## Options considered
- A — consequence
- B — consequence

## Decision
What is now authoritative?

## Why
Evidence/tradeoff that supports it.

## Consequences
What downstream work may rely on, and what this makes harder.

## Revisit trigger
Optional: what new evidence would justify reopening it.
```

For architecture decisions with durable consequences, use the project's ADR convention when one exists.

## Rulings

A **ruling** resolves an execution ambiguity without pretending it is a permanent architecture decision.

Use:

```text
RUL-003: <what was decided> — <why this is the best reversible path> — <cost if wrong>
```

Rulings let a controller keep moving through reversible ambiguity.

Escalate a ruling into a formal decision when downstream Agents will rely on it broadly or reversal becomes expensive.

## Stop vs rule

Prefer a documented ruling when:
- options are reversible
- the specification gives enough intent to choose
- the downside of a wrong choice is bounded rework
- waiting costs more than the likely rework

Stop for authority when:
- action is destructive or meaningfully irreversible
- production/public/external side effect needs approval
- security-sensitive action requires authorization
- expenditure or contractual commitment is involved
- business/policy intent is genuinely unknown
- every plausible path materially changes the agreed outcome

## Escalation packet

When stopping, make the escalation actionable:

```markdown
## Decision required
<single question>

### Why it blocks
<packets or project DoD affected>

### Evidence
<what we know>

### Options
A. <tradeoff>
B. <tradeoff>

### Recommendation
<preferred choice and why>

### Cost of delay
<only if real>
```

Do not escalate questions an Agent can resolve by reading existing authoritative material or performing a bounded investigation.
