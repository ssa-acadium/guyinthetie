# Evidence and Delivery Confidence

## Purpose

Use this reference when deciding what evidence is required to trust a work packet, integration gate, release, migration, or completed program.

The objective is **confidence proportional to consequence**.

## Evidence hierarchy

Prefer, in order:

1. governing specification, contract, policy, or acceptance requirement
2. reproducible system evidence from the actual project
3. automated test or verification output
4. independent expert review tied to explicit criteria
5. demonstrated engineering practice relevant to the situation
6. established local convention with a record of working
7. reasoned heuristic
8. bounded experiment

A lower-ranked source is not useless. It simply carries less authority. Label heuristics and experiments so downstream Agents do not mistake them for requirements.

## Evidence packet

A completed work packet should return a compact evidence package:

```markdown
## Completion report — PKT-###

### Deliverables
- <artifact / path / commit / endpoint>

### DoD results
- PASS — <criterion> — <evidence>
- PASS — <criterion> — <evidence>

### Verification performed
- <command / review / measurement>

### Decisions made
- <decision/ruling IDs>

### Residual risks or limitations
- <explicit accepted condition or none>

### Downstream contract
- <what the next packet may now safely assume>
```

Avoid long implementation diaries unless needed for diagnosis. The controller needs artifacts, criteria, evidence, decisions, and guarantees.

## Confidence proportional to risk

Increase validation depth when failure can:
- lose or corrupt data
- expose secrets or unauthorized access
- cause irreversible user/business effects
- break a public or shared interface
- affect many components
- create expensive operational recovery
- remain latent until production

Reduce ceremony for low-risk, reversible, mechanically verifiable work.

## Release confidence

Before release or external handoff, ask whether the evidence covers:

### Functional
- required behavior works
- failure/negative paths are covered
- important user journeys are validated

### Integration
- interfaces compose in the target environment
- versions/configuration are compatible
- migrations and consumers agree on contracts

### Security
- applicable controls are implemented and tested
- secrets/permissions/configuration are correct
- newly introduced attack surfaces were reviewed where warranted

### Reliability and operations
- health/observability is sufficient
- failure detection is possible
- recovery or rollback is known and feasible
- operational owner knows what to watch

### Delivery mechanics
- build/deploy path works from the intended source
- environment-specific configuration is explicit
- required approvals are satisfied

### Documentation
- user/operator/developer docs reflect current behavior where needed
- durable decisions exist for future maintainers

Not every project needs every category. Omit deliberately, not accidentally.

## DORA metrics

When a team operates a production delivery system, DORA metrics can help diagnose flow and stability. Treat them as system indicators over time, not developer scorecards.

Useful current measures:
- change lead time
- deployment frequency
- failed deployment recovery time
- change fail rate
- deployment rework rate

The value is in understanding trends and constraints within a comparable application/service context.

A metric ceases to be useful when the team optimizes the number instead of the delivery system.

## Operational acceptance

A software feature may be technically correct but operationally incomplete.

Consider whether someone can answer:
- How do we know it is healthy?
- How do we know it is failing?
- Who owns the response?
- Can we reverse or recover the change?
- What state/data must be preserved?
- What dependency or credential can expire?
- Where is the procedure documented?

If these questions matter to the risk profile and have no answer, the project may not be Done.

## Evidence quality traps

### "Tests passed"
Insufficient when the tests do not cover the stated acceptance criteria. Tie evidence to criteria.

### "Reviewed by Agent X"
Insufficient without the review surface and acceptance standard.

### "Works on my machine"
Useful local evidence, not deployment/integration evidence.

### "Industry best practice"
Not evidence that the mechanism fits this project. Name the requirement or failure mode it addresses.

### "No errors observed"
Absence of observed failure is weaker than a test designed to expose the relevant failure.

### Screenshots as proof
Useful for visual state, weak for hidden behavior, repeatability, security, or data integrity.

## Program completion evidence

The controller should be able to construct a final manifest:

```markdown
| Project DoD criterion | Evidence | Artifact/version | Status |
|---|---|---|---|
| ... | ... | ... | PASS |
```

If a criterion has no current evidence, it is not complete merely because all contributing packets are closed.
