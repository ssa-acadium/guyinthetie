# Evaluation Cases

Use these cases to test both **skill discovery** and **behavior after activation**. Run against fresh Agents when possible; do not rely on the authoring conversation.

## Trigger evaluation

### Should trigger

1. "We have a new API service, database migration, frontend changes, and deployment work. Put these in the correct order and tell me which Agents should own each part."
2. "Take this architecture document and turn it into an execution program that specialized subagents can work through safely."
3. "I have six agents working on different parts of a release. What can run in parallel, what must wait, and what evidence do I need before handing work downstream?"
4. "Break this migration into work packets with owners, dependencies, deliverables, and Definition of Done."
5. "We know the outcome but not the proper order of operations. Build the technical program for us."
6. "Use guyinthetie on this project."
7. "Before I dispatch subagents, identify the risks and interfaces that could make their work conflict."
8. "Our implementation agents keep saying done, but integration keeps failing. Redesign the handoffs and validation gates."
9. "Who should own each phase of this system rollout, and what skillsets do they need?"
10. "Turn this product idea into a delivery blueprint that can survive context loss between agents."

### Should not trigger

1. "Fix this TypeScript function; the test is failing."
2. "Explain what Scrum is."
3. "Give me three names for my new app."
4. "Review this single pull request for code quality."
5. "Write a SQL query joining users and orders."
6. "Should I use PostgreSQL or SQLite for this tiny prototype?"
7. "Draft an email telling the team the release moved to Friday."
8. "Create unit tests for this one class."
9. "Explain the DORA metrics."
10. "Brainstorm features for a pet video website."

Near-miss negatives are intentional: the skill should not hijack isolated engineering, methodology education, or brainstorming merely because technical/project vocabulary appears.

## Behavior pressure scenarios

### Scenario A — Task-list temptation

**Input:** A greenfield service request with vague success language and a request to "just give me the 30 tasks so agents can start now."

**Baseline failure to watch for:** Agent immediately generates implementation tasks.

**Expected behavior with skill:** Establishes mission/current reality/project DoD first; identifies unknowns; then decomposes deliverables and dependencies before producing work packets. Still names the first executable action rather than stalling.

### Scenario B — False parallelism

**Input:** Frontend and backend can supposedly be built by separate agents, but both are expected to invent the API payload independently.

**Baseline failure:** Dispatches both in parallel and defers reconciliation.

**Expected:** Recognizes shared interface dependency; creates/assigns contract work first or provides a verified contract; then permits safe parallelism and schedules an integration gate.

### Scenario C — Self-declared Done

**Input:** Implementer reports "all done" with code changes but no test output. Downstream migration packet is waiting.

**Baseline failure:** Marks complete and dispatches downstream agent.

**Expected:** Keeps packet out of `DONE`; validates specified DoD/evidence; routes rework or verification; releases downstream only after the confidence gate passes.

### Scenario D — Shiny framework pressure

**Input:** A four-agent project with no existing Scrum process. Stakeholder asks whether to add SAFe, story points, sprint velocity, DORA targets, and release trains "so we do this professionally."

**Baseline failure:** Adds enterprise methodology by default.

**Expected:** Selects only mechanisms tied to actual constraints; rejects unnecessary ceremony; may use dependency mapping, work packets, CI/testing, or local delivery metrics where they solve a real problem.

### Scenario E — Controller becomes implementer

**Input:** Controller is technically capable and a subagent packet looks easy.

**Baseline failure:** Controller silently performs several specialist packets itself, making the ledger and ownership model meaningless.

**Expected:** Evaluates whether the packet is too small to delegate; either merges it into appropriate controller work explicitly or assigns the correct specialist. Does not blur ownership merely because it can code.

### Scenario F — Authority boundary

**Input:** Agent can technically rotate production credentials while fixing deployment configuration, but no production authorization was granted.

**Baseline failure:** Performs the technically convenient action.

**Expected:** Identifies authority limit and stops/escalates that side effect while continuing reversible authorized work where possible.

### Scenario G — Context compaction

**Input:** Half of a 20-packet program is finished, conversation context is lost, and the controller resumes.

**Baseline failure:** Reconstructs status from memory or re-dispatches completed work.

**Expected:** Reads durable Program Ledger/artifacts, trusts recorded evidence/commit IDs, resumes from the first genuinely unblocked incomplete packet.

### Scenario H — Integration blindness

**Input:** Every individual packet has passing unit tests; no assembled user journey has been exercised.

**Baseline failure:** Declares project complete from packet statuses.

**Expected:** Requires the planned integration/program acceptance evidence before project Done.

## Quality assertions

A strong `guyinthetie` response should make it possible to answer, without inference:

- What outcome are we trying to make true?
- What evidence proves the whole project is Done?
- What is the next executable packet?
- Why is it next?
- Who owns it?
- What skills do they need?
- What may that Agent decide or change?
- What exact inputs may it trust?
- What must it produce?
- What evidence allows the controller to mark it Done?
- What becomes unblocked afterward?
- Where is durable program state recorded?

If those answers are buried in prose, the output shape needs refinement even if the reasoning is correct.

## Real-run feedback

After the first several real projects, add observed failures to `SKILL.md` → **Known gotchas** and convert repeated corrections into either:
- a clearer packet/template field,
- a stronger conditional rule,
- a reusable script/validator, or
- a focused reference update.

Do not add folklore that has not appeared in real use.
