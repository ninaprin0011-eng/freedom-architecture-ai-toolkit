# Prompt 05 Test Run — Portfolio & Interview Reviewer

> This is an illustrative prompt test using a fictional learner and a deliberately incomplete portfolio evidence set. It is not a review of the repository owner, and the lab evidence below must not be represented as professional experience.

## Test objective

Verify that Prompt 05 scores only supported evidence, handles incomplete categories without artificially assigning zeroes, evaluates critical gates separately, catches inflated career claims, and begins an evidence-grounded mock interview with one question rather than supplying answers.

## Fixture input

**Target role:** Junior-to-mid DevOps Engineer.

**Project:** Reliable Application Delivery on Kubernetes — personal/local lab.

**Repository revision:** fictional commit `abc1234` supplied for the fixture.

**Evidence supplied:**
- `app.py`: `/health` and `/version` HTTP endpoints.
- `tests/test_app.py`: health, version, and unknown-route tests.
- Local test output: 3 tests passed.
- Kubernetes Deployment excerpt with a readiness probe.
- Troubleshooting record showing a readiness probe configured for `/ready`, an observed HTTP 404, live-configuration inspection, correction to `/health`, and supplied recovery output showing `1/1 Ready` and `1/1 Available`.
- README states this is a personal/local Kubernetes lab.
- Draft resume bullet below.

**Not supplied:**
- Dockerfile or container build/run evidence.
- Helm chart or Helm validation evidence.
- CI workflow or CI run evidence.
- Second failure/recovery exercise.
- Clean-checkout verification.
- Full architecture diagram/runbook.
- Evidence that the learner can explain the project without AI.

### Draft resume bullet

> Built and deployed a production-ready Kubernetes platform with automated CI/CD, Helm, and advanced incident recovery, ensuring highly available application delivery.

### Learner contribution statement

> I created the API and tests in a personal lab, worked through the readiness-probe failure exercise, and used AI to help structure documentation and review the troubleshooting logic. I have not deployed this project to production. Docker, Helm, and CI are planned but are not part of the evidence supplied for this review.

## Expected review behavior

### Rubric assessment

| Category | Score | Fixture evidence / rationale |
|---|---:|---|
| 1. Role relevance and skill mapping | 2 | API, testing, Kubernetes validation, and troubleshooting are relevant, but major planned DevOps components are not yet evidenced. |
| 2. Application and automated tests | 3 | Three supplied test results cover both valid endpoints and an unknown route. |
| 3. Docker/container quality | Not Assessed | No Dockerfile or build/run evidence supplied. |
| 4. Kubernetes deployment and validation | 3 | Supplied readiness and Deployment availability evidence demonstrates the stated local-lab behavior. |
| 5. Helm packaging | Not Assessed | No chart or validation evidence supplied. |
| 6. CI/CD correctness and security | Not Assessed | No workflow or run evidence supplied. |
| 7. Troubleshooting and recovery | 2 | One evidence-backed recovery exercise is present; the rubric gate requires two. |
| 8. Documentation and reproducibility | 1 | Lab status is disclosed, but clean-checkout verification and complete runbook/architecture evidence are missing. |
| 9. Interview explanation and trade-offs | Not Assessed | No learner interview answer has been evaluated yet. |

**Score:** 11 / 20 assessed points across 5 of 9 categories.

Do **not** convert this to `19.8/36`, do not apply the rubric's full 36-point readiness bands, and do not treat four Not Assessed categories as zeroes. The incomplete evidence set is itself important to the final status.

### Critical release gates

| Gate | Status | Reason |
|---|---|---|
| No exposed secrets/confidential data | Pass for supplied fixture | None appear in the supplied evidence; this is not a claim about unseen repository files. |
| Clean-checkout setup verified | Not Assessed | No result supplied. |
| Automated tests run accurately reported | Pass | Supplied result shows three tests passed. |
| Docker image build/application verified | Not Assessed | No evidence supplied. |
| Kubernetes resources/connectivity verified | Pass for stated local-lab scope | Supplied readiness and Deployment availability results support the stated recovery. |
| Helm lint/render/install tested if in scope | Not Assessed | Planned but no evidence supplied. |
| CI passes valid changes and blocks a failing test | Not Assessed | No CI evidence supplied. |
| Two failure/recovery exercises documented | Fail | Only one exercise supplied. |
| README distinguishes lab/simulation/professional experience | Pass | Fixture says README labels the project a personal/local lab. |
| Learner can explain major components without AI | Not Assessed | Requires interactive interview evidence. |

### Critical blockers

1. The resume bullet materially overstates the evidence: `production-ready`, automated CI/CD, Helm, advanced incident recovery, and high availability are unsupported.
2. The rubric requires two documented failure/recovery exercises; only one is supplied.
3. Reproducibility is incomplete because a clean-checkout verification is missing.
4. Major planned DevOps components—containerization, Helm, and CI—cannot yet be reviewed.

### Truthful replacement resume/project bullet

> Built and tested a small HTTP API in a personal Kubernetes lab, validated Kubernetes readiness behavior, and documented diagnosis and recovery of a misconfigured readiness probe; expanding the project with container, Helm, and CI/CD evidence.

This wording deliberately identifies the work as a lab, states only evidenced accomplishments, and labels unfinished areas as expansion rather than completed functionality.

### Portfolio presentation status

**Needs fixes.** The supplied evidence demonstrates useful application-testing and Kubernetes troubleshooting work, but a critical gate fails and several core project areas remain unassessed. This status concerns the portfolio evidence only; it is not a prediction of employment readiness or hiring outcome.

### Interview coverage plan

The interactive interview should test:
- Why readiness is different from process `Running` state.
- How the learner knew the 404 was caused by the probe/application contract mismatch.
- Why `/health` was chosen instead of disabling the probe.
- What evidence proved recovery.
- What the basic local server would need before production use.
- What the learner personally wrote versus what AI helped structure.

## First mock-interview question

Your pod was `Running` but remained `0/1 Ready`. Walk me through the evidence that led you from that symptom to the readiness-probe path mismatch, and explain how you verified that your fix actually recovered the Deployment.

## Prompt quality verdict

**PASS for this fixture.** The revised prompt prevents an incomplete portfolio from receiving a misleading full-scale score, evaluates release gates independently, catches a strongly inflated resume claim, preserves the distinction between lab and professional work, and starts the mock interview with one evidence-grounded question without supplying the learner's answer.