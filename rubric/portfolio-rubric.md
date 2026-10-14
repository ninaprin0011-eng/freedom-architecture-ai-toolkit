# Portfolio Assessment Rubric

Score each category from 0–4 based on evidence, not file presence. Mark Not Assessed when evidence is unavailable.

| Score | Definition |
|---:|---|
| 0 | Missing, incorrect, or unsafe |
| 1 | Partial; major gaps or unsupported claims |
| 2 | Works in part; important gaps remain |
| 3 | Meets stated criteria with reproducible evidence |
| 4 | Strong evidence, clear trade-offs, and thoughtful limitations |

## Categories
1. Role relevance and skill mapping
2. Application and automated tests
3. Docker/container quality
4. Kubernetes deployment and validation
5. Helm packaging
6. CI/CD correctness and security
7. Troubleshooting and recovery
8. Documentation and reproducibility
9. Interview explanation and trade-offs

Maximum: 36 points.

## Provisional interpretation
- **29–36:** Strong portfolio candidate if every critical gate passes.
- **22–28:** Useful foundation; address priority gaps.
- **0–21:** More implementation or verification needed.

These pilot bands are not validated predictors of hiring outcomes. A high score cannot compensate for a critical blocker.

## Critical release gates
- [ ] No exposed secrets, credentials, or confidential employer data.
- [ ] Clean-checkout setup instructions verified.
- [ ] Automated tests run and results accurately reported.
- [ ] Docker image builds and application behavior verified.
- [ ] Kubernetes resources and connectivity verified in stated environment.
- [ ] Helm chart lint/render/install tested if in scope.
- [ ] CI passes valid changes and blocks a deliberately failing test.
- [ ] Two failure/recovery exercises documented with evidence.
- [ ] README distinguishes lab, simulation, cloud, and professional experience.
- [ ] Learner can explain major components and limitations without AI.

## Review report format
1. Scope and evidence reviewed.
2. Scores with evidence.
3. Critical blockers.
4. Highest-priority improvements.
5. Unassessed areas.
6. Truthfulness/security review.
7. Mock interview questions.
8. Status: Ready for presentation / Needs fixes / Not enough evidence.