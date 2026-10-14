# Example 06 — Prompt 01 Test Run (Job Description Analyzer)

> **Purpose:** Validate the revised prompt against realistic posting text and a clearly fictional learner profile. This is a demonstration, not a recommendation about a specific person's qualifications. Posting text was reviewed on 2026-10-14; posting publication dates were not visible in the reviewed pages. Recheck each source before using this analysis for an active application.

## 1. Test inputs

### Target profile (fictional)
- Target: DevOps / Kubernetes Engineer, early-to-mid level
- Seniority: approximately 2–4 years relevant experience
- Geography: flexible for this test; an actual learner must specify location and work authorization constraints
- Goal: build a credible public portfolio without implying lab work is professional experience

### Self-assessment (fictional)
Ratings are self-reported. Evidence notes are intentionally brief and do not independently verify proficiency.

| Skill | Rating | Evidence type | Evidence note |
|---|---:|---|---|
| Linux/CLI | 2 | Lab/Personal Project | Basic administration and command-line troubleshooting |
| Git/GitHub | 3 | Lab/Personal Project | Uses branches, commits, pull requests |
| Kubernetes | 3 | Professional | Has deployed workloads and helped troubleshoot EKS issues; scope not independently verified |
| Docker | 2 | Lab/Personal Project | Built and ran a container image |
| Helm | 1 | Lab/Personal Project | Read and made small edits to a chart |
| AWS | 3 | Professional | Has supported workloads on AWS; exact services and ownership need detail |
| Infrastructure as code | 2 | Lab/Personal Project | Completed a small Terraform exercise |
| CI/CD | 2 | Lab/Personal Project | Built or modified a basic pipeline |
| Scripting | 2 | Lab/Personal Project | Small Bash/Python automation tasks |
| Observability/troubleshooting | 3 | Professional | Participated in troubleshooting; artifacts and outcomes not yet linked |
| Security practices | 1 | Lab/Personal Project | Basic familiarity; no concrete security artifact yet |

## 2. Posting inventory

| ID | Posting | Seniority / context | Evidence limitation |
|---|---|---|---|
| P1 | [PDI Technologies — DevOps Engineer II](https://jobs.lever.co/pditechnologies/39542b34-d973-4d2c-bf24-07b1bcd64207) | 3–5 years; on-site in Hyderabad, Chennai, or Bangalore | Posting date not visible in reviewed text; page text accessible |
| P2 | [Netomi — DevOps Engineer I](https://jobs.lever.co/netomi/ffe81537-5d1b-437e-a5e8-43546aa8c655) | At least 2 years; remote, Gurugram/India context | Posting date not visible in reviewed text; page text accessible |
| P3 | [Magnet Forensics — SRE/DevOps Engineer](https://jobs.lever.co/magnetforensics/efd7e6e1-2cde-4010-8b75-b9500cfdf748) | 3+ years; operational SRE/DevOps responsibilities | Posting date and geography should be confirmed directly |

**Fit caveat:** These postings are useful for testing technical extraction, but they do not establish fit for a learner targeting US-based work. Geography, work authorization, remote-work eligibility, and seniority alignment must be checked before treating this as a target-role market scan.

## 3. Skills matrix

Frequency means the skill or a defensible equivalent appears in the posting text, not that every employer requires the same depth. Requirement strength is preserved separately.

| Skill | Evidence by posting | Frequency | Target-role interpretation | Learner evidence / gap | Suggested proof and acceptance test | Confidence |
|---|---|---:|---|---|---|---|
| Kubernetes / EKS | P1: working Kubernetes and EKS; Deployments, Services, ConfigMaps, Secrets, Ingress, storage, troubleshooting. P2: Kubernetes management and RBAC requirements. P3: EKS operations and workload troubleshooting. | 3/3 | Core explicit signal across all three; EKS operations named in P1/P3. | Rating 3, professional self-report; scope and artifacts not supplied. | Deploy a small API with Deployment and Service; document probes, resource requests, configuration, and a deliberately broken workload with diagnosis. A reviewer can reproduce deploy and recovery from README steps. | High for posting evidence; medium for learner gap |
| Helm | P1: working knowledge. P2: chart development/management in responsibilities and requirements. P3: working experience. | 3/3 | Repeated signal; depth varies by posting. | Rating 1, lab; clear gap relative to these postings. | Package the app as a chart with values for two configurations; helm lint and template checks pass; document upgrade and rollback. | High |
| CI/CD | P1: build/test/package/deploy pipelines and quality gates. P2: build and maintain CI/CD pipelines. P3: GitLab CI/CD working experience. | 3/3 | Strong common signal; exact tool differs. | Rating 2, lab. | GitHub Actions workflow runs tests and image build on pull request; failed tests block the workflow; README shows successful and failed runs. This does not prove GitLab/Jenkins experience. | High |
| Infrastructure as code / Terraform | P1: Terraform and IaC qualifications. P2: Terraform explicitly described as mandatory. P3: Terraform IaC listed as a working requirement. | 3/3 | Strong signal; P2 specifically calls Terraform mandatory for that role, not universally. | Rating 2, lab. | Add a small local or low-cost Terraform configuration; formatting and validation pass; document plan review, state considerations, cleanup, and limits. | High |
| AWS / cloud | P1: hands-on AWS and named services. P2: familiarity with AWS/GCP/Azure. P3: hands-on AWS and named services. | 3/3 for cloud/AWS context; hands-on AWS explicit in P1/P3 | Strong signal. Distinguish general cloud familiarity from hands-on AWS requirements. | Rating 3, professional self-report; exact services and ownership need detail. | Add an architecture diagram and service-specific evidence only for services actually used; label portfolio-only work clearly. | High for posting evidence; medium for learner gap |
| Scripting | P1: PowerShell, Bash, or Python. P2: Python, Ruby, or Go. P3: Python and Bash. | 3/3 | Common signal; one language does not imply proficiency in all named languages. | Rating 2, lab. | Create a script that validates project prerequisites or summarizes test/deployment status; add tests, usage examples, and error handling. | High |
| Linux administration | P1: Linux and/or Windows administration. P3: Linux administration. P2: no direct Linux requirement in reviewed text. | 2/3 | Common signal, not universal in this sample. | Rating 2, lab. | Include a troubleshooting lab using logs, process/network commands, permissions, and a reproducible runbook. | High |
| Docker / containers | P1: Docker containers explicitly. P3: container patching and vulnerability remediation, but Docker not explicitly named in reviewed text. P2: no explicit Docker mention in reviewed text. | 1/3 for Docker | Relevant to portfolio and explicit in P1; generic container references are not counted as Docker-specific. | Rating 2, lab. | Build a small image, run as non-root, scan it, and document image size and security trade-offs. | High |
| Observability | P1: Datadog/Grafana/Prometheus/CloudWatch examples and incident/root-cause work. P2: continuous monitoring and service-mesh observability responsibilities. P3: Datadog or comparable tooling and alert triage. | 3/3 for monitoring/observability concepts | Common operational theme; named tools are not interchangeable proof of hands-on use. | Rating 3, professional self-report; evidence not linked. | Add a health endpoint, meaningful logs, a dashboard or local metrics view, and an incident runbook. Show detection and verification after remediation. | Medium-high |
| Security / access control | P1: security scanning preferred; Kubernetes Secrets/IAM in operational context. P2: RBAC/access control requirements. P3: least-privilege IAM, secrets, patching, network segmentation. | 3/3 for related security/access themes, with different requirement strength | Relevant, but Kubernetes RBAC, AWS IAM, secret handling, and image scanning should remain distinct subskills. | Rating 1, lab. | Demonstrate least-privilege Kubernetes RBAC, safe secret-handling without committing secrets, and a container scan. Include negative tests showing unauthorized access is denied. | Medium-high |
| GitOps / Argo CD | P1: preferred GitOps tools such as Argo CD. P2: Argo CD listed among CI/CD tool examples. P3: working experience with Argo CD and sync troubleshooting. | 3/3 mentions; requirement strength varies | Useful differentiator and explicit working requirement in P3, but not equally prioritized by every employer. | No rating supplied in this test profile. | Optional extension after core CI/CD and Helm: deploy from a GitOps repo and document sync drift/recovery. | High |

## 4. Prioritized learning plan

1. **Helm fundamentals:** current self-rating is lowest among repeated technical signals. Convert the Kubernetes workload into a chart and prove install, values override, upgrade, and rollback.
2. **CI/CD quality gates:** improve the basic pipeline so tests and image checks must pass before merge/build completion. Explain which deployment steps are simulated versus actually deployed.
3. **Terraform/IaC proof:** create a small, reviewable example with validation and safe cleanup. Keep Terraform and cloud-specific experience claims precise.
4. **Security evidence:** add RBAC/least-privilege checks, safe secret-handling documentation, and a container scan. Never commit credentials.
5. **Operational proof:** add observable health, a reproducible failure, diagnosis, recovery, and a runbook. This makes troubleshooting claims inspectable without presenting lab work as production work.

## 5. Issues detected and prompt quality verdict

- **Seniority mismatch handled:** PDI and Magnet ask for roughly 3+ years; Netomi says at least 2 years. A learner targeting a junior role should not treat every senior-role requirement as baseline.
- **Frequency and priority separated:** Kubernetes, Helm, CI/CD, and Terraform appear repeatedly, but requirement strength differs.
- **Named tools not conflated:** GitHub Actions portfolio evidence is not the same as hands-on GitLab CI, Jenkins, or Argo CD experience.
- **Evidence gap surfaced:** professional self-ratings have no links or outcome descriptions in this test, so the output requests proof rather than treating ratings as verified.
- **Source limitation visible:** publication dates and geographic eligibility need confirmation. Replace mismatched postings with ones aligned to the learner's actual target geography before making job-search decisions.

**Verdict:** The revised prompt passes this test with one remaining workflow improvement: confirm the learner's actual target geography and seniority, then replace any mismatched postings. No further change to Prompt 01 is required from this run.
