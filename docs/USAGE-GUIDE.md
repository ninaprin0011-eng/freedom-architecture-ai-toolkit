# Usage Guide

Use these five assets as a guided workflow for producing a credible DevOps/Kubernetes portfolio. Each asset has a master prompt, required inputs, expected outputs, and an evidence gate. Do not skip the handoff evidence between stages.

## 1. Analyze actual job postings
Use `prompts/01-job-description-analyzer.md` with three real postings and the job-posting/self-assessment templates.
- Record the source URL and date checked.
- Separate required, preferred, and responsibility-only mentions.
- Distinguish stated requirements from AI interpretation.
- Treat proficiency ratings as self-reported and evidence strength separately.
- Save accepted results as `docs/skills-matrix.md`.

**Handoff to Step 2:** target role/seniority, prioritized gaps, evidence strength, and any posting/geography limitations.

## 2. Plan the capstone
Use `prompts/02-portfolio-project-planner.md` with the skills matrix, study time, environment, existing project state, and budget constraints.
- Keep the MVP small and coherent; separate stretch goals.
- Map each priority gap to a feature, objective acceptance test, and evidence artifact.
- Include milestone estimates, dependencies, recovery considerations, and buffer.
- Prefer local/low-cost options; make cloud services optional unless required by the learning objective.
- Save the approved plan as `docs/project-plan.md`.

**Handoff to Step 3:** select exactly one milestone, its acceptance criteria, repository state, environment/tool versions, and tests already run.

## 3. Implement incrementally
Use `prompts/03-devops-project-scaffolder.md` for one milestone at a time.
1. State the milestone boundary and acceptance criteria.
2. Review complete proposed files or focused patches for internal consistency.
3. Run validation commands in a safe local/disposable environment.
4. Record actual output rather than assuming generated code works.
5. Commit only changes you understand.
6. Record limitations and the next step.

Do not ask the scaffolder to generate the entire repository in one response. Do not proceed to the next milestone until the current milestone has the evidence required by the plan or is explicitly marked blocked/deferred.

**Handoff to Step 4:** expected behavior, actual behavior, environment/recent changes, sanitized output, relevant configuration, and commands already run.

## 4. Verify and troubleshoot
Use `prompts/04-verification-troubleshooting-assistant.md` when behavior differs from the acceptance criteria.
- Separate confirmed facts from hypotheses.
- Start with low-risk, read-only diagnostics.
- Use one discriminating check at a time and state what each possible result means.
- Do not treat a restart or disappearance of a symptom as root-cause proof.
- Once evidence supports a cause, make the smallest reversible remediation.
- Verify both the original failure condition and an independent recovery signal where practical.
- Record the incident in `templates/incident-report.md` and update the runbook.

**Handoff to Step 5:** exact repository revision, verification evidence, failure/recovery records, documentation, and explicit statements of what is lab, simulated, AI-assisted, professional, or still planned.

## 5. Review the portfolio and practice the interview
Use `prompts/05-portfolio-interview-reviewer.md` with the exact repository revision and actual evidence.
- Score only supported categories; use **Not Assessed** when evidence is unavailable.
- Show partial scores as `earned / assessed maximum`; do not extrapolate them to 36.
- Evaluate critical release gates separately from rubric scores.
- Flag unsupported resume/project claims and rewrite them to match the evidence.
- Treat portfolio presentation readiness as different from predicting hiring success.
- Begin the mock interview with one evidence-grounded question at a time.

## Evidence gate

A generated file is not proof of a working system. Preserve command output, test results, CI links, environment/tool versions, and commit references. Clearly distinguish professional experience from lab/personal projects, simulated fixtures, AI-assisted material, and planned work. Never paste secrets or confidential employer data into an AI assistant.

## Tested examples

The prompt-specific test runs are `examples/06-prompt-01-test-run.md` through `examples/10-prompt-05-test-run.md`. Use them to understand expected prompt behavior, not as evidence for your own portfolio. The learner must produce and preserve their own verification results.
