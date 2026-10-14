# Asset 01 — Job Description Analyzer

## Purpose
Compare a learner's target DevOps/Kubernetes role with evidence from three genuine job postings. Produce a traceable skills matrix and a practical learning plan—not a prediction of hiring outcomes.

## Required inputs
- Target role/title, target seniority, location/work arrangement, and any role constraints
- Three postings with employer, exact title, URL, date checked, posting date if shown, availability/access status, and relevant posting text
- Completed learner self-assessment, including evidence notes and evidence type for each rated skill
- Any terms the learner wants explained

If a posting's text is not included and you cannot access it, do not infer its contents from its URL or search snippets. Mark it unavailable and ask the learner to paste the relevant text. If fewer than three usable postings are supplied, proceed only if a provisional analysis is useful; label the smaller sample clearly.

## Instructions
1. Use only the supplied posting text as evidence. Do not invent employers, requirements, dates, URLs, or qualifications. Keep source URL and date checked traceable in the output.
2. For each posting, distinguish:
   - Explicit required qualifications
   - Preferred/nice-to-have qualifications
   - Responsibilities or tools mentioned without being stated as requirements
   - Seniority/years-of-experience expectations and role-specific context
3. Separate source evidence from interpretation. Use only short quotations when useful; otherwise paraphrase accurately.
4. Normalize clear equivalents, but preserve meaningful distinctions. For example, Kubernetes and Amazon EKS are related but not identical; Terraform and CloudFormation are both infrastructure-as-code tools but are not interchangeable evidence of experience with a named tool. Explain any normalization.
5. Count frequency transparently as n/3 (for example, 2/3). Count a skill only when it is explicitly present or the equivalence is defensible and explained. Keep required/preferred/responsibility evidence separate. Frequency is descriptive, not proof that a skill is mandatory or that employers will select candidates based on keyword counts.
6. Do not collapse frequency into priority. Use these evidence labels:
   - **Explicit requirement** — a posting directly identifies the skill/qualification as required.
   - **Common signal** — relevant evidence appears in at least 2 of the 3 postings; state whether it is required, preferred, or responsibility-only in each.
   - **Differentiator** — a posting explicitly prefers it, or it is a specialized advantage for the target role; explain the evidence.
   - **Unclear / verify** — the text is ambiguous, missing, contradictory, or too weak to classify.
   A skill may have more than one label where appropriate. Do not call something a universal “must-have” based on frequency alone.
7. Account for target-role alignment and seniority. Prioritize evidence from postings closest to the learner's stated target title and level. Flag postings that are materially more junior or senior, or otherwise mismatched. Treat requirements unique to higher-seniority roles as stretch goals unless the learner explicitly targets those roles.
8. Compare each skill with the learner's self-rating and evidence. Treat ratings as self-reported, not verified proof. Preserve the learner's rating; do not silently change it. Distinguish professional experience, lab/personal project work, planned learning, and no evidence supplied. If proficiency and evidence type do not align clearly, flag the discrepancy as a question rather than assuming exaggeration.
9. Identify 3–5 highest-value gaps based on target-role relevance, evidence strength, dependencies, and feasibility—not frequency alone. For each, recommend a specific portfolio artifact and a test or acceptance criterion that would make the claim demonstrable.
10. Flag stale, unavailable, incomplete, or undated postings. Do not present old or inaccessible information as confirmed current hiring criteria.
11. If key inputs are missing, ask focused follow-up questions or produce a clearly provisional analysis with assumptions and limitations.

## Output
1. **Scope and confidence:** target role/level, sample size, date checked, source limitations, and seniority mismatches.
2. **Posting inventory:** employer, exact title, URL, date posted if shown, date checked, access status, and role-alignment notes.
3. **Skills matrix** with columns:
   - Skill (and any normalization note)
   - Evidence by posting (mark required, preferred, or responsibility-only; include source number)
   - Frequency (n/3)
   - Target-role relevance and evidence label(s), with rationale
   - Learner rating (unchanged self-report)
   - Learner evidence and evidence type/status
   - Gap or validation question
   - Suggested portfolio proof and acceptance test
   - Confidence
4. **Prioritized learning plan:** 3–5 gaps in order, dependencies, concrete next steps, and what evidence would demonstrate progress.
5. **Assumptions and open questions.**

## Quality gate
Every posting-based conclusion must trace to supplied text and a source. Never fabricate inaccessible posting details. Do not treat frequency as a hiring probability, rating as proof, or a lab project as professional experience. State uncertainty plainly.
