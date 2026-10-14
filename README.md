# Freedom Architecture AI Toolkit
## DevOps & Kubernetes Portfolio Edition

**Version:** 0.1.0  
**Status:** Pilot — prompts and templates require learner review and validation.

This toolkit helps working IT professionals turn real job requirements into a focused technical portfolio, build it incrementally, verify results, and prepare to explain the work in interviews.

It is an AI-assisted workflow, not an autonomous engineer or a promise of employment. Review and verify all AI-generated code, configuration, analysis, and recommendations.

## The five assets

1. **Job Description Analyzer** — prioritize requirements from genuine job postings; output `docs/skills-matrix.md`.
2. **Portfolio Project Planner** — map skill gaps to a realistic project and acceptance criteria; output `docs/project-plan.md`.
3. **DevOps Project Scaffolder** — generate and review files one milestone at a time.
4. **Verification & Troubleshooting Assistant** — diagnose failures from evidence and verify recovery; output troubleshooting notes and a runbook.
5. **Portfolio & Interview Reviewer** — assess evidence and rehearse interview explanations.

## Recommended workflow

Job postings → skills matrix → project plan → incremental implementation → verification and troubleshooting → portfolio review and mock interview.

The pilot capstone is **Reliable Application Delivery on Kubernetes**: a small API, automated tests, a container image, Kubernetes Deployment and Service, Helm chart, CI workflow, two controlled failure/recovery exercises, and reproducible documentation.

## Repository contents

- `prompts/` — reusable master prompts
- `templates/` — learner input and output templates
- `examples/` — illustrative sample outputs
- `rubric/` — shared assessment rubric and release gates
- `docs/` — usage, safety, and changelog

## Principles

- **Evidence over assertion:** generated files are not proof that they work.
- **Truthful career claims:** distinguish professional experience, lab work, and planned work.
- **Small, reviewable changes:** scaffold one milestone at a time.
- **Security first:** never paste secrets, customer data, private employer information, or production credentials into an AI assistant.
- **Learner ownership:** be able to explain, test, troubleshoot, and defend the project without AI.
- **Transparent limitations:** label assumptions, unknowns, and unverified claims.

## Versioning

This toolkit uses semantic versioning as a practical convention. See [the changelog](docs/CHANGELOG.md).

## Disclaimer

Educational material provided as-is. AI outputs may be incomplete or wrong. Verify commands and configuration in a safe environment. This toolkit does not guarantee interviews, offers, or job placement.
