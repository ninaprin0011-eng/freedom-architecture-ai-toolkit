# Project Plan: Reliable Application Delivery on Kubernetes

> Status: Proposed plan. Do not mark tasks complete until the stated checks have been run and evidence saved.

## 1. Goal and reviewer
- What should a reviewer learn from this project?
- Target role and seniority:
- Intended reviewer (technical interviewer, peer engineer, hiring manager):
- Success criteria:

## 2. Inputs, constraints, and assumptions
- Skills matrix / priority gaps:
- Weekly study time:
- Target completion date:
- Operating system and hardware:
- Local cluster/tool options:
- Cloud access and approved budget ceiling:
- Existing repository/project state:
- Accessibility or tooling constraints:
- Assumptions requiring confirmation:

## 3. Target-role alignment
| Priority gap | Why it matters for target role | Planned feature | Acceptance test | Evidence artifact | Included? / reason |
|---|---|---|---|---|---|
| | | | | | |

## 4. Scope
### Minimum viable portfolio (MVP)
- [ ] Small API with health/version endpoint
- [ ] Automated tests for expected and invalid behavior
- [ ] Container image with documented build/run steps
- [ ] Kubernetes Deployment and Service, validated in named environment
- [ ] Helm chart with values and documented install/upgrade path
- [ ] CI workflow with a test gate
- [ ] Two controlled failure/recovery exercises
- [ ] README, architecture diagram, runbook, limitations, and clean-checkout instructions

For every item, note if it is deferred and why. Never imply an unchecked item is complete.

### Optional stretch goals
- [ ] Container image scan
- [ ] Additional observability
- [ ] GitOps (for example, Argo CD)
- [ ] Cloud deployment (only with explicit access/budget approval)
- [ ] Other:
- What would trigger deferring each stretch goal?

## 5. Architecture and flows
- Components:
- Request flow:
- Source/build/test/image flow:
- Deployment flow:
- Local vs simulated vs cloud components:
- Security boundaries and secrets handling:
- Architecture diagram location:

## 6. Milestones and acceptance criteria
| Milestone | Dependencies | Tasks | Estimate (hours) | Objective acceptance test | Evidence to save | Risks / recovery |
|---|---|---|---:|---|---|---|
| App and tests | | | | | | |
| Container | | | | | | |
| Kubernetes | | | | | | |
| Helm | | | | | | |
| CI | | | | | | |
| Failure/recovery labs | | | | | | |
| Documentation/review | | | | | | |

## 7. Weekly schedule and buffer
| Week | Planned outcomes | Hours available | Buffer / fallback |
|---|---|---:|---|
| | | | |

## 8. Cost, security, and cleanup
- Maximum approved spend:
- How costs will be monitored:
- Cloud resources (if any):
- Cleanup command/steps:
- Secret and credential handling:
- Log/screenshot sanitization:
- No-cloud fallback:

## 9. Scope cuts and exit criteria
1. First item to defer:
2. Second item to defer:
3. Features that must remain for the project to be coherent:
4. Definition of done:
5. What evidence must be present before publication:

## 10. Portfolio and interview checklist
- [ ] Clean-checkout setup verified
- [ ] Tests and results documented
- [ ] Image build/run verified
- [ ] Kubernetes resources/connectivity verified in the stated environment
- [ ] Helm lint/render/install verified if in scope
- [ ] CI passes valid changes and blocks a failing test
- [ ] Two failures, diagnoses, fixes, and recovery checks documented
- [ ] Diagram, README, runbook, limitations, and cost/security notes reviewed
- [ ] Learner can explain design decisions without AI
- Likely interview questions:
- Trade-offs and limitations to acknowledge:

## 11. Open questions and status
- Unknowns requiring confirmation:
- Commands/tests not yet run:
- Current status: Proposed / In progress / Verified / Blocked
