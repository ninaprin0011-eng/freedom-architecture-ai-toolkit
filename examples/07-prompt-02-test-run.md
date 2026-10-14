# Example 07 — Prompt 02 Test Run (Portfolio Project Planner)

> **Test status:** Plan generated for a fictional learner. This is a proposed plan only; no project code or infrastructure was executed during this planning test. Estimates are illustrative and must be revised for the learner's actual environment.

## 1. Test inputs

- **Target:** early-to-mid-level DevOps / Kubernetes Engineer
- **Goal:** credible public GitHub portfolio for technical interviews
- **Time:** 5 hours/week for 6 weeks (30 hours total)
- **Environment:** Linux laptop, Git/GitHub, Docker or compatible container runtime
- **Kubernetes:** kind or Minikube; availability not yet confirmed
- **Cloud:** no cloud deployment approved; assume $0 spend and local-only execution
- **Existing experience (fictional):** basic API/testing, Docker, CI/CD, and Terraform practice; limited Helm and security evidence
- **Priority gaps:** Helm, CI quality gates, security proof, reproducible troubleshooting. Terraform/IaC also appears in postings but need not be forced into this capstone.

## 2. Goal and architecture

Build a small HTTP API with health and version endpoints, test it, package it as a container, deploy it to local Kubernetes, manage configuration through Helm, and validate the workflow in CI. Demonstrate two controlled failures, diagnose them, and prove recovery.

**Flow:** source code → unit tests → container build → CI quality gate → local Kubernetes deployment through Helm → request/health checks → failure exercises and runbook.

The app, container, cluster, and Helm execution are local. CI uses GitHub Actions. No cloud runtime or production deployment is included.

## 3. Scope

### Minimum viable portfolio
- API with /health and /version endpoints.
- Automated tests for healthy behavior and at least one invalid/error path.
- Reproducible container build/run; test non-root execution where feasible.
- Kubernetes Deployment and Service, validated in the named environment.
- Helm chart with configurable image/tag and documented install/upgrade.
- GitHub Actions workflow that runs tests and builds the image; failing tests must fail the workflow.
- Two controlled failure/recovery labs with evidence:
  1. **Bad image tag:** deployment cannot start; identify image-pull failure, correct the tag, and verify rollout and endpoint.
  2. **Incorrect readiness path or port:** workload fails readiness; inspect events/logs, fix configuration, and verify ready endpoints and a successful request.
- README, architecture diagram, setup instructions, runbook, evidence links, and limitations.

### Deferred / not claimed
- **Terraform and cloud resources:** deferred to a separate project because this 30-hour capstone focuses on end-to-end application delivery. This plan does not demonstrate Terraform proficiency.
- **Argo CD/GitOps:** optional only after the MVP.
- Production-grade monitoring, high availability, load testing, secrets-management platforms, and production operations are out of scope.
- Cloud deployment is excluded unless access and a cost ceiling are explicitly approved.

## 4. Milestones and acceptance tests

| Milestone | Estimate | Dependencies | Objective acceptance test | Evidence to save |
|---|---:|---|---|---|
| API and tests | 4 h | Runtime/language selected | Clean checkout runs tests; health/version endpoints return documented responses; invalid behavior is tested | Test files, command/output, commit |
| Container | 3 h | API/tests pass | Image builds; container starts and responds; documented run command works; non-root execution tested or limitation documented | Container file, build/run output |
| Kubernetes | 5 h | Image works; local cluster available | Apply resources; Deployment becomes available; Service is reachable by documented method; cleanup works | Manifests, kubectl checks, environment/version notes |
| Helm | 4 h | Kubernetes deployment works | helm lint and render checks pass; install/upgrade succeeds locally; values override changes a documented setting | Chart, values, command output |
| CI quality gate | 4 h | Tests and build defined | Pull-request workflow runs tests/build; a deliberately failing test produces a failed workflow; restored test returns to green | Workflow file and successful/failed run links |
| Failure/recovery labs | 4 h | Kubernetes and Helm usable | Both failures are reproduced; symptom, diagnosis, fix, and post-fix verification are documented | Incident notes, sanitized events/logs, before/after checks |
| Documentation/review | 4 h | Core milestones done | Clean checkout follows README; diagram matches files; status claims match evidence; learner answers review questions without AI | README, diagram, runbook, evidence index |
| Explicit buffer | 2 h | — | Used for setup/debugging; if exhausted, cut stretch scope | Note unresolved blockers |

**Estimated total:** 26 hours planned work plus 2 hours explicit buffer = 28 hours, leaving 2 hours of the 30-hour budget as additional reserve. These are estimates, not guarantees.

## 5. Six-week schedule

| Week | Focus | Hours | Exit condition |
|---|---|---:|---|
| 1 | API and tests | 5 | Tests pass locally; endpoints documented |
| 2 | Container build/run | 5 | Container behavior verified |
| 3 | Kubernetes Deployment/Service | 5 | Workload and connectivity verified locally |
| 4 | Helm chart | 5 | Lint/render/install/upgrade checks pass |
| 5 | CI quality gate and first failure lab | 5 | CI blocks failing test; first recovery evidence saved |
| 6 | Second failure lab, docs, clean-checkout review | 5 | Both labs documented; README/runbook/diagram match implementation |

If cluster setup takes longer than expected, switch to a suitable local Kubernetes option or record the blocker. Never replace actual verification with a claim that it works.

## 6. Risks, cost, and security

- **Cluster setup:** check memory, virtualization, container runtime, and installation requirements before scheduling Kubernetes work.
- **Tool drift:** record Docker/compatible runtime, Kubernetes, kubectl, and Helm versions.
- **Time overrun:** defer stretch goals first; preserve tests, CI failure gate, and evidence for both failure/recovery exercises.
- **Cost:** no cloud resources are planned. If cloud is later approved, define a budget ceiling, identify chargeable resources, and document cleanup before provisioning.
- **Security:** never commit tokens, credentials, kubeconfig files, or sensitive logs. Use synthetic examples and sanitize output.
- **Accuracy:** distinguish verified results from assumptions and blocked steps.

## 7. Scope-cut order

1. Cut Argo CD/GitOps, extra observability, and cloud deployment.
2. Cut optional image scanning if it threatens the deadline; record the limitation and consider it later.
3. Keep API tests, container build/run, Kubernetes/Helm validation when the environment supports it, CI test gate, two controlled failure/recovery exercises, and accurate documentation.
4. If local Kubernetes is unavailable, mark Kubernetes/Helm acceptance criteria **Blocked / Not verified**. Publish only what was actually tested and state the environment gap.

## 8. Definition of done and interview readiness

- Clean checkout follows documented steps in the stated environment.
- Every “passed” acceptance test has evidence.
- CI shows a passing run and a deliberately failing test.
- Both failure/recovery exercises include symptom, diagnostic evidence, fix, and recovery verification.
- Diagram and README match the repository.
- Learner can explain container vs. Kubernetes responsibilities, Deployment vs. Service, Helm values, CI gates, failure diagnosis, and limitations without AI.
- README identifies this as a local portfolio lab, not production experience.

## 9. Test findings and verdict

**Pass:** The planner produces a sequenced MVP with objective tests, effort estimates, buffer, security/cost guardrails, failure/recovery evidence, and scope cuts.

**Important correction:** Terraform appeared in the source job postings, but the planner does not force it into a time-boxed capstone. It explicitly defers Terraform and therefore does not claim this project demonstrates it. This avoids keyword-driven scope creep and unsupported skill claims.

**Open questions before adopting this for a real learner:** confirm target geography/seniority, preferred language, RAM/disk, container runtime, local Kubernetes option, actual weekly hours, and deadline.
