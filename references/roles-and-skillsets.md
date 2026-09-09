# Roles, Skillsets, and Authority

## Purpose

Use this reference when assigning work to Agents or Subagents.

A reliable plan distinguishes three things that are often collapsed:

- **Role** — who is accountable for the outcome
- **Skillset** — what competence the work actually requires
- **Authority** — what decisions or side effects the Agent is allowed to make

One Agent may hold several roles. One role may require several skillsets. Capability does not imply approval authority.

## Assignment rule

Choose the Agent for the packet, not the packet for the Agent.

For each packet, answer:

1. What professional role should own this outcome?
2. What technical/domain skills are necessary?
3. What level of judgment is required?
4. What tools and access are necessary?
5. What decisions may the Agent make independently?
6. What requires review or another authority?
7. Does the validator need independence from the implementer?

## Common technical program roles

Use these as functional labels, not mandatory headcount.

| Role | Typical accountability |
|---|---|
| Technical Program Manager / Controller | Program sequencing, dependencies, risks, state, handoffs, completion evidence |
| Product / Business Owner | Desired outcome, scope, priority, policy, business acceptance |
| Solution / Software Architect | System boundaries, interfaces, architectural decisions, cross-component consequences |
| Tech Lead | Technical execution strategy, engineering consistency, local design judgments |
| Software Engineer | Implementation and unit/component verification |
| Platform / DevOps Engineer | Build/deploy pipeline, infrastructure, environments, configuration, operational automation |
| Security Engineer | Threat analysis, secure design, controls, security verification |
| Data Engineer / DBA | Data models, migrations, integrity, performance, recovery |
| QA / Test Engineer | Acceptance strategy, test design, independent verification |
| SRE / Operations | Reliability, observability, incident/recovery readiness, production behavior |
| UX / Design | User interaction, accessibility, design intent, usability evidence |
| Technical Writer / Documentation Owner | Durable operational/user/developer documentation |
| Reviewer / Validator | Independent compliance/quality/evidence check for a bounded packet |

Avoid assigning an exotic role when an existing generalist can competently perform the function. Preserve the role label so responsibility remains intelligible.

## Skillset naming

Name concrete capabilities rather than vague labels.

Weak:
- backend skills
- cloud expert
- security knowledge

Better:
- TypeScript, Node.js, REST API design, PostgreSQL transactions
- Docker, GitHub Actions, Netlify deploy configuration, secrets management
- OAuth 2.0/OIDC, threat modeling, OWASP ASVS, session security

The skillset list helps the controller select the right Agent/model and tells the assignee what kind of judgment the packet expects.

## Authority contract

Every consequential packet should state authority explicitly.

Example:

```markdown
### Authority
May:
- change implementation inside `src/auth/`
- add tests and internal helpers
- update non-breaking internal interfaces

May not without controller approval:
- change the public API contract
- add a new identity provider
- rotate production secrets
- deploy to production
```

This prevents a technically capable Agent from expanding scope simply because it can.

## Reviewer independence

Independent review is valuable when:
- security boundaries change
- data migration or deletion is involved
- architecture or public interfaces change
- a large multi-file change has broad blast radius
- implementation evidence is subjective
- the implementer made consequential assumptions

For review, prefer giving the validator:
- packet requirements
- authoritative specification
- resulting artifacts/diff
- test/evidence outputs

Do not lead with the implementer's narrative. The reviewer should reconstruct whether the requirements were met rather than inherit the implementer's framing.

Low-risk mechanical work may use self-review if independent review adds little confidence.

## Model / Agent capability selection

Match capability to judgment, not prestige.

- **Mechanical, exact work** — a fast/less costly Agent is often sufficient when requirements are complete and verification is objective.
- **Integration/debugging** — use an Agent with stronger reasoning and broad codebase comprehension.
- **Architecture, security, ambiguous tradeoffs, final system review** — use the strongest relevant reasoning capability available.
- **Repeated rework** — escalate capability or change the role if the same Agent repeatedly fails the same acceptance boundary.

The cheapest successful path is preferable to an expensive default, but false economy creates extra turns, rework, and context cost.

## Player-coach boundary

`guyinthetie` may understand architecture and code deeply enough to challenge assumptions and formulate work precisely. Its default role is to coordinate and verify rather than opportunistically absorb specialist implementation.

If the controller starts doing the task because "it is faster," ask whether:
- the packet is too small to justify delegation
- the available Agent lacks a required skill
- the packet contract is incomplete
- this is genuinely controller work rather than specialist work

Do not create handoffs for their own sake, but do not collapse all work into the controller merely because it is technically capable.
