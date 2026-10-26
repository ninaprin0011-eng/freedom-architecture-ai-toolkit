# Changelog

## 0.2.0 — Tested workflow release
- Tested and revised all five reusable prompts with realistic or explicitly labeled fixture inputs.
- Strengthened job-analysis handling of requirement type, frequency, seniority, evidence strength, and stale/undated postings.
- Strengthened project planning with constraints, acceptance tests, evidence artifacts, effort budgets, scope cuts, and no-cloud fallbacks.
- Strengthened scaffolding to enforce one-milestone scope, internally consistent files, meaningful tests, secure defaults, and explicit execution status.
- Strengthened troubleshooting to separate facts from hypotheses, prioritize read-only diagnostics, require causal evidence, and verify recovery.
- Strengthened portfolio review to score only supported evidence, preserve Not Assessed categories, evaluate release gates independently, catch inflated claims, and begin evidence-grounded mock interviews.
- Added prompt test runs `examples/06-prompt-01-test-run.md` through `examples/10-prompt-05-test-run.md`.
- Updated README and usage guidance with explicit evidence handoffs between all five assets.
- Corrected and expanded the toolkit manifest to track the current repository inventory.

### Compatibility and behavior notes
- Prompt outputs are stricter about distinguishing planned, generated, locally tested, CI-tested, deployed, lab, simulated, AI-assisted, and professional work.
- Partial portfolio scores must no longer be extrapolated to the full 36-point rubric.
- Existing learner projects can continue using the templates, but should adopt the stronger evidence/status distinctions before portfolio review.

## 0.1.0 — Initial pilot release
- Added five reusable master prompts.
- Added learner input and output templates.
- Added illustrative sample outputs.
- Added shared 0–4 assessment rubric and release gates.
- Added usage and safety guidance.

## Release policy
Review changes to prompts, templates, rubric, examples, and evidence handoffs together. Update this file and `toolkit-manifest.json` for each release and note compatibility or behavior changes.
