# Example 11 — End-to-End Learner Workflow Validation

> **Purpose:** Validate that Freedom Architecture v0.2.0 carries one fictional learner's evidence consistently from Prompt 01 through Prompt 05. This is an integration test, not a claim about the repository owner or a real job candidate. Job-posting evidence comes from the Prompt 01 test reviewed on 2026-10-14; recheck live postings before using them for an application.

## 1. Fictional learner and target

- Target: early-to-mid DevOps / Kubernetes Engineer
- Relevant experience target: approximately 2–4 years
- Environment: Linux laptop; local Kubernetes; no approved cloud spend for the capstone
- Available time: 5 hours/week for 6 weeks = 30 hours
- Career-claim rule: professional self-reports remain distinct from personal/lab evidence

Key self-ratings carried from Prompt 01 include Kubernetes 3 (professional self-report), Helm 1 (lab), CI/CD 2 (lab), IaC 2 (lab), scripting 2 (lab), AWS 3 (professional self-report), observability/troubleshooting 3 (professional self-report), and security 1 (lab). These ratings are not treated as independently verified proficiency.

## 2. Prompt 01 → market signals and evidence gaps

The three test postings repeatedly surfaced Kubernetes, Helm, CI/CD, Terraform/IaC, cloud, scripting, observability, and security/access themes. The integration test carries forward the following priorities rather than recomputing them:

| Signal/gap | Prompt 01 evidence | Handoff requirement |
|---|---|---|
| Kubernetes | 3/3 postings; learner rating 3 professional self-report | Build reproducible local deployment evidence without replacing professional claims |
| Helm | 3/3; learner rating 1 lab | Include chart validation and install/upgrade evidence |
| CI/CD | 3/3; learner rating 2 lab | Include an automated quality gate and both passing/failing evidence |
| Terraform/IaC | 3/3; learner rating 2 lab | Keep as a gap, but allow scope cut if 30-hour/no-cloud constraints require it |
| Scripting | 3/3; learner rating 2 lab | Application/test automation can contribute evidence but must not imply every named language/tool |
| Security/access | related themes 3/3; learner rating 1 lab | Demonstrate safe defaults and truthful limitations |
| Troubleshooting | operational theme across postings | Produce controlled failure/recovery evidence and a runbook |

**Integration check:** PASS. Prompt 01 outputs are specific enough to become project acceptance criteria, while preserving tool distinctions such as GitHub Actions vs GitLab/Jenkins and local Kubernetes vs EKS.

## 3. Prompt 02 → constrained project plan

The accepted capstone is **Reliable Application Delivery on Kubernetes**. The 30-hour budget is carried forward exactly: 28 planned hours plus a 2-hour buffer.

| Milestone | Hours | Prompt 01 gap addressed | Required evidence |
|---|---:|---|---|
| API and tests | 4 | scripting/testing foundation | test command and actual results |
| Container | 3 | containers/security | build/run result; non-root/safe-default review where feasible |
| Kubernetes | 5 | Kubernetes | Deployment/Service, rollout/readiness/connectivity evidence |
| Helm | 4 | Helm | lint/render/install or documented scope/status |
| CI | 4 | CI/CD | passing run plus deliberately failing test gate |
| Failure/recovery labs | 4 | troubleshooting/operations | two documented failures, diagnosis, fix, recovery evidence |
| Documentation/review | 4 | reproducibility/interview explanation | README, diagram, runbook, limitations, clean-checkout evidence |
| Buffer | 2 | schedule risk | used only if needed |

Terraform is intentionally deferred from the MVP because the no-cloud, 30-hour capstone must remain coherent. This does **not** erase the Prompt 01 Terraform gap; it records it as a future portfolio item instead of pretending the capstone closes every market gap.

**Integration check:** PASS. The planner converts high-priority gaps into evidence-producing milestones and makes an explicit scope cut rather than silently dropping the IaC gap.

## 4. Prompt 03 → first implementation milestone

The scaffolder is given only the **API and tests** milestone, not the whole project. The tested fixture generated:

```text
app.py
tests/test_app.py
```

The API implements `GET /health` and `GET /version`; the tests cover both successful routes and an unknown route. The actual Prompt 03 isolated-environment validation recorded Python 3.13.5 and three passing tests.

Status carried forward:

- API source: **generated and locally tested in the Prompt 03 isolated test environment**
- Learner-machine verification: **not supplied**
- Container: **planned, not implemented in this integration evidence**
- Kubernetes: **planned at this handoff**
- Helm: **planned**
- CI: **planned**
- Production deployment: **not demonstrated**

**Integration check:** PASS. Prompt 03 does not jump ahead to Docker, Kubernetes, Helm, or CI, and its evidence status is not upgraded beyond what was actually tested.

## 5. Prompt 04 → troubleshooting evidence

For integration testing, the later Kubernetes milestone uses the established application contract: `/health` and `/version` return 200 and unknown routes return 404.

The fictional troubleshooting fixture then supplies a pod that is `Running` but `0/1 Ready`, with Kubernetes reporting an HTTP 404 from a readiness probe configured for `/ready`. The assistant first inspects the live Deployment configuration, confirms the mismatch, then recommends changing only the readiness path to `/health`.

Recovery fixture evidence shows:

- rollout completed successfully;
- replacement pod became `1/1 Ready`;
- Deployment became `1/1 Available`.

Status carried forward:

- Failure scenario 1: **verified within supplied fictional fixture evidence**
- Real learner cluster execution: **not demonstrated by this integration test**
- Failure scenario 2: **missing**

**Integration check:** PASS. The failure is causally linked to an endpoint created in Prompt 03, so troubleshooting is not an unrelated canned exercise. Recovery status remains explicitly fixture-scoped.

## 6. Prompt 05 → portfolio and interview review

The final review receives only the evidence actually accumulated above. It must not infer completion of the remaining Prompt 02 milestones.

Expected assessment behavior:

| Category | Integration status |
|---|---|
| Role relevance / skill mapping | Assessable from Prompt 01 + project plan |
| Application/tests | Assessable from Prompt 03 test evidence |
| Container | Not Assessed in this evidence chain |
| Kubernetes | Assessable only to the extent of supplied fictional Kubernetes fixture evidence |
| Helm | Not Assessed |
| CI/CD | Not Assessed |
| Troubleshooting/recovery | Partially assessable; only one of two required exercises exists |
| Documentation/reproducibility | Partial; end-to-end learner clean-checkout proof is absent |
| Interview explanation | Not Assessed until the learner answers interactively |

An inflated claim such as:

> Built a production-ready Kubernetes platform with automated CI/CD, Helm, and advanced incident recovery.

must be rejected. A truthful integration-stage description is:

> Built and tested a small HTTP API as part of a personal Kubernetes portfolio lab and documented diagnosis and recovery of a readiness-probe configuration failure; container, Helm, CI/CD, a second failure exercise, and full reproducibility evidence remain to be completed and verified.

The mock interview should begin from the actual evidence chain, for example by asking the learner to explain why the pod could be Running but not Ready, how the 404 narrowed the diagnosis, and what evidence demonstrated recovery. It should not provide the answer before the learner responds.

**Integration check:** PASS. Prompt 05 consumes earlier evidence without converting planned milestones into completed accomplishments.

## 7. Cross-prompt traceability matrix

| Prompt 01 signal | Prompt 02 plan | Prompt 03/04 evidence | Prompt 05 treatment | Result |
|---|---|---|---|---|
| Kubernetes | Deployment/Service + validation | readiness failure/recovery fixture | assess only supplied local-lab/fixture evidence | PASS |
| Helm | 4-hour milestone | no evidence in chain | Not Assessed | PASS |
| CI/CD | 4-hour milestone | no evidence in chain | Not Assessed | PASS |
| Terraform/IaC | explicit scope cut | no evidence | remains an open gap; no claim | PASS |
| Scripting/testing | API + automated tests | three tests passed in isolated Prompt 03 environment | assess application/tests with environment caveat | PASS |
| Security | safe defaults throughout | loopback local API; no credentials; no privilege workaround | acknowledge limited evidence, do not overclaim | PASS |
| Troubleshooting | two controlled exercises planned | one readiness exercise supplied | partial evidence; two-exercise release gate fails | PASS |

## 8. Integration findings

### What works

1. **Evidence lineage is preserved.** A market signal becomes a planned artifact, then evidence or an explicit missing item, then an interview/review topic.
2. **Scope cuts remain visible.** Terraform is not lost simply because it was excluded from the 30-hour MVP.
3. **Status does not silently escalate.** Generated, locally tested, fixture-verified, learner-verified, CI-tested, and production-deployed remain distinct.
4. **The prompts reinforce each other.** The `/health` endpoint generated in the implementation milestone becomes part of a later Kubernetes troubleshooting exercise.
5. **Missing evidence survives to the reviewer.** Helm, CI, container evidence, a second failure exercise, clean-checkout proof, and learner interview performance remain open rather than being inferred.

### Gaps exposed by the integration test

1. The workflow needs a compact **handoff/status artifact** that travels between prompts; otherwise learners may repeatedly paste long outputs and accidentally lose evidence provenance.
2. The project plan should explicitly retain **deferred market gaps** so they remain visible at final review.
3. The reviewer benefits from an evidence ledger containing artifact, environment, command, result, date, and status—not just narrative summaries.
4. The integration test cannot declare the capstone complete because several planned milestones intentionally have no implementation/verification evidence.

## 9. Release conclusion

**v0.2.0 integration verdict: PASS WITH FOLLOW-UP IMPROVEMENTS.** The five prompts form a coherent evidence-preserving workflow for this fictional learner. No cross-prompt defect requires rolling back v0.2.0. The highest-value next change is to add a lightweight handoff/evidence-status template for v0.2.1, then run a fuller learner validation that actually completes container, Kubernetes, Helm, CI, both failure exercises, documentation, clean-checkout verification, and the interactive interview.
