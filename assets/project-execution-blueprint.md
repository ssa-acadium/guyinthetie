# Project Execution Blueprint

Use this as a flexible default. Remove sections that do not help the project; add project-specific sections when they materially improve execution confidence.

# <Project / Mission Name>

## 1. Mission

**Desired outcome:**  
<What should be true when the program succeeds?>

**Why it matters:**  
<Business/user/operational reason>

**Non-goals:**
- <Explicitly outside scope>

**Constraints:**
- <Time / budget / technology / policy / security / compatibility>

**Unacceptable failures:**
- <Loss, corruption, outage, security, contractual, or other critical failure>

## 2. Current Reality

**System state:**
- <Architecture / code / environment / existing workflow>

**Authoritative inputs:**
- <Specs / repositories / docs / contracts / standards>

**Existing decisions:**
- <Decision ID or concise statement>

**Known unknowns:**
- <Unknown and why it matters>

## 3. Project Definition of Done

| Criterion | Verification / evidence |
|---|---|
| <Observable required state> | <How it will be proven> |

## 4. Deliverable Manifest

| ID | Deliverable | Consumer / purpose | Acceptance boundary |
|---|---|---|---|
| DEL-001 | <artifact/result> | <who/what needs it> | <what makes it acceptable> |

## 5. Roles and Authorities

| Role | Responsibilities | Required skillsets | Authority / limits |
|---|---|---|---|
| <role> | <what this role owns> | <concrete capabilities> | <may / may not> |

## 6. Dependency Model

### Hard prerequisites
- <PKT-X → PKT-Y because...>

### Information dependencies
- <decision / discovery / credential / measurement>

### Interfaces
- <producer ↔ consumer contract>

### Parallel groups
- <packets safe to execute concurrently>

### Critical path
`<PKT-X → PKT-Y → INT-X → REL-X>`

## 7. Ordered Workflow

| Step / Packet | Objective | Why now | Accountable role | Skillsets | Inputs | Work | Deliverable | Definition of Done | Verification | Dependencies | Risks |
|---|---|---|---|---|---|---|---|---|---|---|---|
| PKT-001 | | | | | | | | | | | |

## 8. Work Packet Contracts

### PKT-001 — <Name>

**Objective**  
<One coherent result>

**Program context**  
<Where this fits>

**Why now**  
<Dependency/risk rationale>

**Accountable Agent role**  
<Role>

**Required skillsets / capabilities**
- <skill>

**Tools / access**
- <repo / environment / connector / API / hardware>

**Authority**
- May: <actions/decisions>
- May not without approval: <actions/decisions>

**Inputs**
- <exact artifact / version / decision / interface>

**Verified preconditions**
- <fact that must be true before dispatch>

**Constraints**
- <boundary>

**Non-goals**
- <nearby excluded work>

**Work**
1. <bounded activity>
2. <bounded activity>

**Deliverables**
- <artifact / system state / report>

**Definition of Done**
- <observable criterion>

**Verification / evidence**
- <test / command / reviewer / measurement>

**Handoff target**  
<downstream packet / integration gate / owner>

**Escalate when**
- <condition outside authority or materially invalidating assumption>

## 9. Integration Gates

### INT-001 — <Integration boundary>

**Consumes:**
- <completed packets/artifacts>

**Proves:**
- <assembled behavior that packet-local validation cannot prove>

**Evidence:**
- <end-to-end test / migration rehearsal / deployment validation / review>

## 10. Risk Register

| ID | Risk condition | Consequence | Exposure | Mitigation | Trigger | Owner | Contingency |
|---|---|---|---|---|---|---|---|
| RISK-001 | | | | | | | |

## 11. Decision Log

| ID | Decision | Why now | Authority | Consequence |
|---|---|---|---|---|
| DEC-001 | | | | |

## 12. Program Ledger

| Packet | State | Owner role | Depends on | Artifact / evidence | Next |
|---|---|---|---|---|---|
| PKT-001 | READY | | | | Dispatch |

Allowed controller states:
- `READY`
- `BLOCKED`
- `REWORK`
- `DONE`

## 13. Final Acceptance Manifest

| Project DoD criterion | Evidence | Artifact / version | Status |
|---|---|---|---|
| | | | |

## Next executable action

**Dispatch / decision:** `<PKT-... or DEC-...>`  
**Why it is ready:** <verified prerequisite and sequence rationale>  
**Expected result:** <what becomes true and what it unblocks>
