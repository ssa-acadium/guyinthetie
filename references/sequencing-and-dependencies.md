# Sequencing and Dependencies

## Purpose

Use this reference when the program has multiple packets, parallel work, integration points, real deadlines, or meaningful uncertainty about order of operations.

The goal is not to make a pretty Gantt chart. The goal is to establish the safest and fastest valid order in which work can become true.

## Dependency-first planning

For every packet, identify what must be true before it begins and what becomes possible after it passes validation.

Classify each dependency:

| Type | Meaning | Typical example |
|---|---|---|
| Hard prerequisite | Work cannot be correct without it | schema must exist before code compiles against it |
| Information dependency | A decision or fact is needed | vendor API behavior must be confirmed |
| Interface dependency | Producer/consumer contract must be agreed | request/response schema |
| Integration dependency | Work can proceed separately but cannot be accepted alone | frontend and backend user flow |
| Environmental dependency | Runtime/config/infrastructure must exist | staging database or secret |
| Authority dependency | A business/security/production decision is required | approval to change retention policy |
| Soft/discretionary | Preferred sequence but not mandatory | documentation draft after implementation |

Do not turn a discretionary convention into a hard dependency without explaining why.

## Deriving the order

Use this priority when deciding what should happen first:

1. prerequisites that make later work possible
2. unknowns capable of invalidating large amounts of downstream work
3. interface/contract decisions required by parallel producers and consumers
4. critical-path work with long lead times or external dependencies
5. early integration opportunities that expose composition errors
6. ordinary implementation work
7. polish that does not change acceptance confidence

This often puts small investigations, interface contracts, and environment setup earlier than feature coding.

## Unknowns as first-class work

An unknown deserves its own bounded packet when:
- the answer can change architecture or vendor choice
- a downstream estimate depends heavily on it
- failure would invalidate several packets
- documentation is insufficient and direct experimentation is required

A spike or investigation must still have:
- question to resolve
- method/bounds
- time or scope limit when appropriate
- evidence expected
- decision it informs

Its deliverable is knowledge with evidence, not production code unless explicitly authorized.

## Parallelism

Parallelize packets only when they are truly independent at the required confidence level.

Safe parallelism usually requires:
- stable interfaces or deliberately isolated surfaces
- no shared destructive resource
- no hidden file/module ownership collision
- independent acceptance criteria
- downstream integration gate identified

Before parallel dispatch, perform a collision scan:

```markdown
| Packet A | Packet B | Shared file/interface/resource | Risk | Ruling |
|---|---|---|---|---|
```

If two Agents will change the same interface independently, that is usually not parallelism; it is deferred conflict.

## Critical path

When a deadline is real, identify the chain of dependent packets that determines earliest completion.

Use critical-path reasoning to answer:
- which delay moves the finish date?
- which packet has schedule float?
- where should scarce specialist capacity go first?
- which external dependency needs active escalation?

Do not obsess over exact duration estimates when uncertainty is high. The dependency chain can be valuable even when durations are ranges.

## Backward planning

Use backward planning when there is a legitimate immovable event such as:
- contractual launch
- regulatory filing
- physical installation window
- coordinated migration
- public event

Start from the required acceptance state and work backward through:
- release/production validation
- rollback readiness
- integration testing
- staging/deployment readiness
- implementation completion
- design/contract decisions
- procurement/access/approval lead times

Do not manufacture urgency around arbitrary dates.

## Integration cadence

Prefer integrating at meaningful boundaries rather than waiting for the end.

Examples:
- validate a real API consumer against the first working provider contract
- run migration against a realistic snapshot before all application changes are finished
- exercise deployment/recovery before release week
- test an end-to-end thin slice before parallel feature expansion

Early integration reduces the amount of completed-looking work that can be invalidated at once.

## Queueing and work in progress

Too much simultaneous work increases unfinished inventory, context switching, merge conflicts, and delayed feedback.

Limit work in progress when:
- validation cannot keep up with implementation
- packets repeatedly sit waiting for integration
- Agents compete for the same environment or specialist
- the controller loses clear program state

Do not maximize Agent utilization at the expense of flow. An idle Agent can be cheaper than a queue of partially completed, stale work.

## Sequencing output

For a complex program, include:

```markdown
## Dependency map
- PKT-001 → PKT-003
- PKT-002 → PKT-003
- PKT-003 → INT-001

## Parallel group A
- PKT-001
- PKT-002

## Critical path
PKT-002 → PKT-003 → INT-001 → REL-001

## First unblockers
1. PKT-001 — establishes contract...
2. PKT-002 — resolves vendor uncertainty...
```

If a visual dependency graph materially clarifies the plan, generate one. Do not substitute a graph for explicit packet contracts.
