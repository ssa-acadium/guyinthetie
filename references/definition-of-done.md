# Definition of Done

## Purpose

Use this reference to define observable completion at both the project and work-packet levels.

A Definition of Done is not a status label. It is the evidence boundary separating "work was attempted" from "the required state now exists."

## Project DoD vs packet DoD

### Project Definition of Done

Proves the mission has succeeded as an integrated outcome.

It may include:
- user/business behavior
- cross-component integration
- security and privacy requirements
- performance/reliability expectations
- data integrity
- migration/recovery behavior
- production/deployment readiness
- documentation and ownership
- required approvals or demonstrations

### Packet Definition of Done

Proves one bounded work packet is safe to hand forward.

It should be specific enough that the controller can validate it without asking the implementer what "done" means.

## Write criteria as observable states

Weak:
- authentication implemented
- tests added
- docs updated
- performance is good

Better:
- requests without a valid session receive the specified 401 response and do not reach protected handlers
- unit tests cover the stated success and failure cases and the repository test command exits successfully
- public API changes appear in `docs/api.md` with the final request/response fields
- p95 latency remains below the agreed threshold under the stated test profile

Prefer outcomes and evidence over activity verbs.

## Four layers of completion

For substantial technical work, consider these layers:

1. **Artifact exists** — code, schema, document, configuration, environment, migration, etc.
2. **Artifact is internally correct** — tests, static checks, review, validation.
3. **Artifact integrates correctly** — consumers, interfaces, runtime composition, real data flow.
4. **Artifact is operable** — deployment, observability, recovery, ownership, documentation as applicable.

Not every packet needs all four. The project closeout often does.

## Acceptance criteria quality test

A criterion is strong when:
- two competent reviewers would reach the same pass/fail conclusion
- the evidence can be produced now, not promised later
- it tests the required behavior rather than incidental implementation details
- it includes relevant negative/failure behavior
- it does not silently expand scope

If a criterion contains "appropriate," "sufficient," "robust," "clean," or "proper" without a measurable or reviewable meaning, sharpen it.

## Evidence types

Use the lightest evidence that creates sufficient confidence:

| Risk/type | Useful evidence |
|---|---|
| Pure function / mechanical change | targeted automated tests + repository checks |
| Public API | contract tests, schema validation, consumer test |
| UI behavior | automated interaction where feasible + visual/manual acceptance for design intent |
| Data migration | dry run, row/invariant checks, rollback/recovery evidence |
| Security boundary | threat/control review + relevant automated/manual security tests |
| Infrastructure/deployment | deployment evidence, health checks, rollback/recovery exercise |
| Performance | reproducible benchmark/load profile and measured result |
| Documentation | reviewer can complete intended procedure using the document |
| Architecture decision | recorded context, decision, alternatives/consequences, affected interfaces |

## DoD ownership

The implementer may propose or clarify packet criteria, but should not unilaterally weaken them after execution begins.

If evidence reveals the criterion is incorrect:
1. identify the contradiction or new fact
2. route the change to the authority that owns the requirement
3. record the decision
4. update downstream assumptions
5. revalidate against the revised criterion

This is specification change, not implementation completion.

## Review surfaces

For independent validation, give the reviewer:
- the packet objective and DoD
- authoritative requirements/specification
- resulting artifacts/diff
- test outputs or other evidence
- relevant upstream contracts

Ask for findings tied to a criterion or a concrete quality defect. Avoid open-ended style review when style is not part of Done.

## Completion language

Use precise states:
- `implemented, not yet validated`
- `validation failed: <criterion>`
- `validated locally; integration gate pending`
- `DONE: packet DoD satisfied`
- `project acceptance pending: <remaining evidence>`

Avoid "basically done," "should work," and "looks good" as program states.
