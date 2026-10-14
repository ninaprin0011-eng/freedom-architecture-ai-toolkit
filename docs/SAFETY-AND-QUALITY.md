# Safety and Quality Rules

## Truth and provenance
- Never invent job postings, dates, citations, qualifications, test results, execution evidence, or employer requirements.
- Label illustrative content and assumptions.
- Distinguish professional experience from personal labs and planned work.
- Do not claim AI-generated code was run unless execution evidence is supplied.

## Secure handling
- Never provide secrets, tokens, private keys, passwords, kubeconfigs, or sensitive environment files to an AI assistant.
- Redact private IPs, account identifiers, customer data, internal hostnames, and confidential employer details where relevant.
- Review generated commands for destructive actions before execution.
- Use least privilege and avoid disabling security controls to make a demo work.

## Engineering quality
- Prefer minimal changes and one milestone at a time.
- Require tests or validation commands appropriate to the change.
- Record assumptions, limitations, and unresolved uncertainty.
- Use safe local environments for fault injection.
- Treat diagnosis as a hypothesis until observable evidence confirms it.
- Do not call a project production-ready merely because it runs locally.

## Learner ownership
The learner should be able to explain major files, demonstrate how the project works, diagnose at least two failures, describe trade-offs, and discuss what would need to change for production use.