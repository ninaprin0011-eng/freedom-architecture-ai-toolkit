# Usage Guide

Use these five assets as a guided workflow for producing a credible DevOps/Kubernetes portfolio. Each asset has a master prompt, required inputs, expected outputs, and an evidence gate.

## 1. Analyze actual job postings
Use `prompts/01-job-description-analyzer.md` with three real postings and the job-posting/self-assessment templates.
- Record the source URL and date checked.
- Distinguish stated requirements from AI interpretation.
- Review every skill rating yourself.
- Save accepted results as `docs/skills-matrix.md`.

## 2. Plan the capstone
Use `prompts/02-portfolio-project-planner.md` with the skills matrix, study time, environment, and budget constraints.
- Keep the project small and coherent.
- Map each skill to a feature and objective acceptance test.
- Make cloud services optional unless required by the learning objective.
- Save the approved plan as `docs/project-plan.md`.

## 3. Implement incrementally
Use `prompts/03-devops-project-scaffolder.md` for one milestone at a time.
1. State the goal and acceptance criteria.
2. Review proposed files or patches.
3. Run commands in a disposable/local environment.
4. Inspect output and tests.
5. Commit only changes you understand.
6. Record limitations and the next step.

Do not ask the scaffolder to generate the entire repository in one response.

## 4. Verify and troubleshoot
Use `prompts/04-verification-troubleshooting-assistant.md` with sanitized errors, logs, configuration excerpts, and commands already run. Start with read-only diagnostics, treat explanations as hypotheses, confirm recovery with a repeatable test, and record evidence in troubleshooting notes and a runbook.

## 5. Review the portfolio
Use `prompts/05-portfolio-interview-reviewer.md` with repository contents and actual verification evidence. Mark unavailable evidence as not assessed; score only what is supported. Practice explaining decisions and limitations in your own words.

## Evidence gate
A generated file is not proof of a working system. Keep command output, test results, CI links, and commit references. Clearly distinguish professional experience from lab/personal projects and planned work. Never paste secrets or confidential employer data into an AI assistant.