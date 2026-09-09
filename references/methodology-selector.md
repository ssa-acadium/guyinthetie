# Methodology Selector

## Purpose

Use this reference when deciding whether a project benefits from Scrum, Kanban, critical-path planning, release coordination, SSDF practices, DORA metrics, SRE concepts, or another delivery method.

The rule is simple:

> Choose the mechanism that addresses the constraint. Do not install a framework for prestige.

## Selection by problem

| Problem | Useful mechanism | Avoid |
|---|---|---|
| Continuous stream of small work | Kanban-style flow, WIP limits, cycle-time observation | artificial sprint commitments if they add no value |
| Cross-team dependency network with real date | dependency map, critical-path reasoning, milestones, backward planning | pretending story points provide calendar certainty |
| Product team already operating healthy Scrum | work within Scrum; preserve existing roles/ceremonies that help | parallel shadow process run by TPM |
| High uncertainty in architecture/vendor/API | bounded spikes, prototypes, decision records | fully scheduling downstream work on guesses |
| Regulated/security-sensitive development | secure-development controls integrated through lifecycle; relevant standards such as NIST SSDF | single late security review as substitute for secure development |
| Frequent production delivery | small batches, CI/CD, automated tests, deployment/recovery evidence | giant release branches and late integration by default |
| Reliability-sensitive production service | SLOs, error-budget reasoning, observability, recovery testing | abstract "five nines" goals with no user/service basis |
| Need to improve delivery system | contextual DORA metrics and local bottleneck analysis | quotas, ranking teams, comparing unlike systems |
| One small bounded task | direct execution with appropriate verification | project-management ceremony |

## Scrum

Use Scrum when the team already benefits from iterative product planning, a stable product goal, regular inspection/adaptation, and the roles/events provide useful coordination.

Do not force every technical program into sprints. Infrastructure migrations, incident remediation, research spikes, and externally constrained rollout programs may need different control mechanisms.

The useful Scrum concept to preserve broadly is a shared **Definition of Done**: work reaching a consistent, inspectable quality state before it is treated as complete.

## Kanban / flow

Use flow-oriented practices when work arrives continuously or bottlenecks matter more than sprint commitment.

Useful measures include:
- work in progress
- queue age
- cycle time
- blocked time
- validation/integration bottlenecks

The objective is smoother completion and faster feedback, not maximizing how many Agents appear busy.

## Critical path and milestone planning

Use when dependencies and dates matter. Build the dependency network first; dates without dependencies are calendar decoration.

Use duration ranges when uncertainty is material. Identify external lead times and long-tail risks explicitly.

## Secure development

For security-relevant systems, integrate secure-development practices into the normal lifecycle. NIST SSDF is a useful organizing reference because it defines practices across preparing the organization, protecting software, producing well-secured software, and responding to vulnerabilities.

Translate applicable controls into packet DoD and evidence rather than adding a generic "security phase" at the end.

## DORA

Use DORA metrics to understand delivery performance of a particular application/service over time and find constraints.

Current DORA software-delivery metrics include:
- change lead time
- deployment frequency
- failed deployment recovery time
- change fail rate
- deployment rework rate

Use them as diagnostic signals. Do not turn them into individual performance metrics, universal targets, or scoreboards across dissimilar systems.

## SRE / error budgets

Use SRE concepts when reliability is an actual product requirement.

An error budget can provide a rational tradeoff between continued change and reliability: if reliability is within the agreed objective, change can proceed; if the budget is exhausted, reliability work takes priority under the agreed policy.

Do not introduce error budgets where there is no service-level objective or meaningful reliability decision to make.

## Technical debt

Do not reserve an arbitrary percentage by doctrine.

Prioritize debt when it:
- causes repeated delivery delay
- creates defects or operational risk
- blocks a needed change
- increases security exposure
- makes validation materially harder
- has a favorable remediation cost versus expected drag

Treat debt reduction as work with its own outcome and evidence.

## Metrics discipline

Use a metric only if you can answer:
1. What decision will this metric inform?
2. What behavior could optimizing it accidentally encourage?
3. Is the comparison population genuinely comparable?
4. Can the team influence it?
5. Is the collection cost justified?

Lines of code, raw ticket counts, utilization, velocity rankings, and story points converted to days are generally poor proxies for delivery value or engineering performance.
