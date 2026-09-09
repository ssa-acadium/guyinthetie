# Operating Model

## Purpose

Use this reference when `guyinthetie` is coordinating substantial work across Agents or Subagents.

The central unit is the **handoff-safe work packet**: one bounded outcome, owned by one accountable Agent role, with explicit inputs, authority limits, deliverables, Definition of Done, evidence, and downstream consumers.

## Controller responsibilities

The controller owns program state rather than implementation details. It:

- frames the mission and project Definition of Done
- maintains the deliverable/dependency model
- decides which packets are ready
- dispatches purpose-built Agents with bounded context
- validates packet evidence
- records durable state in the Program Ledger
- releases downstream work only after upstream confidence gates pass
- schedules integration gates where locally valid work must prove system-level behavior

The controller should not become the hidden implementer. If it repeatedly performs specialist work itself, the packet boundary or role assignment is wrong.

## Work packet contract

Every substantial dispatch should resolve these fields before execution:

| Field | Requirement |
|---|---|
| Packet ID | Stable identifier used in ledger and handoffs |
| Objective | One coherent result, not a bundle of unrelated chores |
| Program context | One or two sentences explaining where this packet fits |
| Why now | The dependency, risk, or opportunity that makes it ready |
| Accountable role | Professional role responsible for the outcome |
| Required skillsets | Actual competencies needed to succeed |
| Tools/access | Repositories, environments, credentials, connectors, hardware, or APIs needed |
| Authority | Decisions/actions this Agent may make |
| Authority limits | Decisions/actions that require another owner |
| Inputs | Exact artifacts, decisions, interfaces, versions, or measurements consumed |
| Preconditions | Facts that must already be verified |
| Constraints | Compatibility, policy, performance, security, schedule, or scope boundaries |
| Non-goals | Nearby work explicitly outside this packet |
| Work | Bounded activities necessary to produce the deliverable |
| Deliverables | Concrete output artifacts or system changes |
| Definition of Done | Observable acceptance criteria |
| Verification | Commands, tests, review, demonstration, measurement, or other evidence |
| Handoff target | Downstream Agent, packet, integration gate, or operational owner |
| Risks/escalation | Conditions that require ruling, rework, or authority escalation |

## Context discipline

A Subagent should not need the controller's entire conversation history.

Give it:

1. the work packet
2. the authoritative project/specification artifacts relevant to that packet
3. verified upstream outputs it consumes
4. decisions already made that constrain its work
5. interfaces it must preserve or produce
6. the exact reporting/evidence contract

Do not give it unrelated brainstorming, abandoned alternatives, or implementation narratives from previous Agents unless they are directly relevant evidence.

This reduces context pollution and makes later verification more independent.

## Packet sizing

A good packet is:

- **coherent** — one specialist can hold the problem in working context
- **bounded** — non-goals and authority limits are clear
- **testable** — completion can be demonstrated independently
- **handoffable** — its output is useful without oral history
- **large enough to matter** — the handoff overhead is justified

Split a packet when:
- it requires materially different specialist judgment
- one part can invalidate another and should be proven first
- outputs have different downstream consumers
- independent review would be clearer on separate surfaces
- context required to complete it becomes broad and unrelated

Merge packets when:
- each is a tiny same-shape edit
- they share the same inputs, role, validation method, and downstream consumer
- separation would add handoff ceremony without increasing confidence

## Confidence gate

The normal flow is:

```text
READY
  ↓ dispatch
EXECUTION
  ↓ report + artifacts
VALIDATION
  ├─ fail → REWORK
  └─ pass → DONE
              ↓
        downstream release
```

Validation asks two separate questions:

1. **Did the Agent produce what the packet required?**
2. **Does the evidence support the claim that it works?**

For low-risk mechanical packets, self-verification may be enough. For high-risk, security-sensitive, architectural, integration, migration, or broad changes, use independent review or an independently executed validation path.

Never promote `DONE` merely because the implementer reports success.

## Rework contract

When validation fails, do not send "please fix".

Return:
- failed DoD criterion
- observed evidence
- expected evidence or behavior
- scope of allowed rework
- any newly discovered constraint

Preserve criteria unless an authorized decision explicitly changes the specification. If the criterion itself was wrong, record that as a program decision rather than silently moving the goalpost.

## Program Ledger

Use a durable file or system of record for substantial multi-Agent work.

Minimum useful shape:

```markdown
# Program Ledger — <mission>

## Project Definition of Done
- ...

## Packet status
| Packet | State | Owner role | Depends on | Artifact/evidence | Next |
|---|---|---|---|---|---|

## Decisions
- DEC-001: ...

## Rulings
- RUL-001: ...

## Risks
- RISK-001: ...

## Integration gates
- INT-001: ...

## Next executable action
- PKT-...
```

Use artifact paths, commit SHAs, version IDs, test reports, issue/PR IDs, or environment identifiers instead of vague phrases such as "the auth work is done."

## Handoff package

When packet A unblocks packet B, hand B the smallest sufficient package:

```markdown
## Upstream handoff: PKT-A
Status: DONE

### Produced artifacts
- <path / commit / endpoint / schema>

### Contract now guaranteed
- <interface or behavior B may rely on>

### Evidence
- <test/review/measurement>

### Decisions that constrain downstream work
- <decision IDs and concise consequences>

### Known limitations / residual risks
- <explicitly accepted conditions>
```

The next Agent should consume guarantees, not reconstruct them from logs.

## Integration gates

Add an integration gate when any of these are true:
- two Agents produce opposite sides of an interface
- data crosses component boundaries
- separate migrations must compose safely
- deployment/configuration assumptions combine
- a user journey spans multiple completed packets
- locally passing tests do not prove assembled behavior

An integration gate is itself a packet with an accountable role, DoD, and evidence.

## Program closeout

Before declaring the project complete:

1. re-read the original mission and project Definition of Done
2. verify every required deliverable against current artifacts
3. run system/integration acceptance checks
4. confirm operational ownership and recovery procedures where relevant
5. surface residual risks and accepted limitations
6. verify durable decisions/documentation exist
7. name the final handoff owner or steady-state operating process

Do not infer project completion solely because every implementation packet is marked `DONE`.
