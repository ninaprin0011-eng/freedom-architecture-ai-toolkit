# Freedom Architecture AI Toolkit
## DevOps & Kubernetes Portfolio Edition

**Version:** 0.2.0  
**Status:** Tested pilot — all five prompts have fixture-based test runs; learner validation is still required.

This toolkit helps working IT professionals turn real job requirements into a focused technical portfolio, build it incrementally, verify results, and prepare to explain the work in interviews.

It is an AI-assisted workflow, not an autonomous engineer or a promise of employment. Review and verify all AI-generated code, configuration, analysis, and recommendations.

## The five assets

1. **Job Description Analyzer** — prioritize requirements from genuine job postings; output `docs/skills-matrix.md`.
2. **Portfolio Project Planner** — map skill gaps to a realistic project and acceptance criteria; output `docs/project-plan.md`.
3. **DevOps Project Scaffolder** — generate and review files one milestone at a time.
4. **Verification & Troubleshooting Assistant** — diagnose failures from evidence and verify recovery; output troubleshooting notes and a runbook.
5. **Portfolio & Interview Reviewer** — assess evidence, identify unsupported claims, and rehearse interview explanations.

## Tested workflow

Job postings → skills matrix → project plan → one-milestone scaffold → verification/troubleshooting → evidence-backed portfolio review → mock interview.

Each handoff preserves evidence and status. Planned work does not become implemented work; generated code does not become tested code; local lab work does not become professional experience; and a partial portfolio score is not extrapolated to a full score.

The pilot capstone is **Reliable Application Delivery on Kubernetes**: a small API, automated tests, a container image, Kubernetes Deployment and Service, Helm chart, CI workflow, two controlled failure/recovery exercises, and reproducible documentation.

## Prompt test runs

- `examples/06-prompt-01-test-run.md` — real-posting analysis fixture and skills-gap workflow.
- `examples/07-prompt-02-test-run.md` — constrained project plan with acceptance tests and effort budget.
- `examples/08-prompt-03-test-run.md` — one-milestone API scaffold with actual isolated local test execution.
- `examples/09-prompt-04-test-run.md` — fictional Kubernetes readiness troubleshooting fixture.
- `examples/10-prompt-05-test-run.md` — incomplete portfolio review, claim checking, and mock-interview entry point.

Test fixtures demonstrate prompt behavior; they are not evidence of a learner's professional experience. Where an example contains supplied command output rather than an executed command, it is labeled accordingly.

## Repository contents

- `prompts/` — reusable master prompts
- `templates/` — learner input and output templates
- `examples/` — illustrative samples and prompt test runs
- `rubric/` — shared assessment rubric and release gates
- `docs/` — usage, safety, and changelog
- `toolkit-manifest.json` — version and tracked-file inventory

## Principles

- **Evidence over assertion:** generated files are not proof that they work.
- **Truthful career claims:** distinguish professional experience, lab work, simulated evidence, AI assistance, and planned work.
- **Small, reviewable changes:** scaffold one milestone at a time.
- **Security first:** never paste secrets, customer data, private employer information, or production credentials into an AI assistant.
- **Learner ownership:** be able to explain, test, troubleshoot, and defend the project without AI.
- **Transparent limitations:** label assumptions, unknowns, and unverified claims.
- **Reproducibility:** preserve commands, actual results, environment details, and relevant commit references.

## Versioning

This toolkit uses semantic versioning as a practical convention. See [the changelog](docs/CHANGELOG.md).

## Disclaimer

Educational material provided as-is. AI outputs may be incomplete or wrong. Verify commands and configuration in a safe environment. This toolkit does not guarantee interviews, offers, or job placement.
