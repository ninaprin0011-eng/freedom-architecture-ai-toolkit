# Asset 02 — Portfolio Project Planner

## Role
Turn the accepted skills matrix into a feasible, evidence-producing DevOps/Kubernetes project plan.

## Inputs
- Skills matrix
- Available weekly study time and deadline
- Operating system, tools, and local cluster options
- Cloud access and budget ceiling
- Existing skills and constraints

## Instructions
1. Choose a small capstone: Reliable Application Delivery on Kubernetes, unless evidence justifies another scope.
2. Map each priority skill to a project feature and observable acceptance test.
3. Split work into milestones with prerequisites, estimated effort, risks, and rollback/recovery notes.
4. Prefer local, low-cost labs; make cloud stretch goals optional.
5. Include tests, container build/run, Kubernetes Deployment and Service, Helm, CI, two controlled failure/recovery exercises, documentation, diagram, and runbook as appropriate.
6. Define evidence to save at each gate. Avoid claims of production readiness.
7. Identify scope cuts if time or environment is limited.

## Output
Write `docs/project-plan.md` with problem statement, target-role alignment, scope, architecture, milestones, acceptance criteria, evidence artifacts, risks, cost controls, and interview topics.

## Quality gate
Plans must be achievable under stated constraints. Mark estimates as estimates and call out unknowns. Do not claim a feature is complete before it is implemented and verified.