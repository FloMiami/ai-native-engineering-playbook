# AI-native engineering playbook — Codex handoff

## Objective
Build a private, version-controlled, platform-independent personal engineering knowledge repository from my reading and practical experiments. Convert learning into original chapter notes, frameworks, workflows, templates, cheat sheets and eventually reviewed Claude Code/Codex skills. Human judgment and accountability remain central. The repository, not chat history, is the source of truth.

## Source and progress
Alfonso Graziano, *AI-Native Software Engineering: Building with AI Agents and Spec-Driven Development*, O’Reilly early release. Chapter 1, The AI-Native Engineer, through “What AI-Native Engineering Is Not.” Chapter incomplete; other chapters not analyzed. Updates reference: https://ainativesoftware.engineering/book/updates. Seven prior discussion entries, including overlapping passages, yielded 42 candidate principles (below); deduplicate without losing meaning. These are original paraphrased study notes and our derived recommendations, not a transcript or independently verified full-book summary.

## Chapter 1 learning entries
1. Failure modes of vibe coding: plausible-looking code can conceal defects; local task optimization causes architectural drift; unstated conventions and constraints are missing context. Examples include service-layer validation, soft deletion, localized errors. Proposed remedies: verification, architecture checks, explicit context.
2. AI-native engineering versus vibe coding: delegate mechanical implementation while retaining human ownership of intent, design, constraints and review. Review AI like a capable contributor new to the codebase; consider untested cases, architecture, maintainability and user needs.
3. Preserve the engineering lifecycle: AI accelerates rather than removes necessary engineering steps. Author argues speed can approach vibe coding; not a measured guarantee. Our extension: use approval gates, acceptance evidence, deployment and rollback controls.
4. Two Engineers, One Task (A): illustrative payment rate-limiting task requires 10 requests/minute per user. Vague prompt led to IP-based limiting, passing tests and production failure: shared IPs wrongly pooled users and changing IPs undermined the policy. Lesson: verify business intent, not only implementation. Our additional concern: introducing dependencies without reviewing existing infrastructure.
5. Same task (B, planning): before prompting, define authenticated user identity, reuse existing user_id, account for idempotent retries, follow metrics conventions, and inspect available cache infrastructure.
6. Same task (B, full): approved cache wrapper and existing same-zone Redis, explicit context, review against notes, identify failed-prior-request edge case, revise spec and rerun. Author's scenario contrasts ten minutes upfront with a day of remediation, not empirical data. Our inference: better specs may reduce rework and token use. Keep evolving specs as durable artifacts.
7. What AI-native engineering is not: not just AI application development, tool fashion, human removal, reduced coding volume or senior-only work. Practices transfer across tools; adopt incrementally starting with largest workflow gap. Four author-identified competencies: specification literacy, verification discipline, risk ownership, systems thinking. Author's career/demand claims are perspective, not independently verified forecasts.

## Candidate principles (42, preserve IDs for traceability)
001. Professional-looking code is not necessarily correct.
002. Optimize the whole system, not just the task.
003. Make engineering conventions explicit.
004. Successful execution does not establish sound architecture.
005. Delegate implementation, not judgment.
006. Treat AI as a capable contributor unfamiliar with the system.
007. Passing tests alone does not establish production readiness.
008. Consider future requirement changes.
009. Retain human ownership of intent, constraints, review and results.
010. Automate tasks, not accountability.
011. Preserve the lifecycle while accelerating execution.
012. Measure reliable delivery, not code volume.
013. Correct implementation may solve the wrong problem.
014. Resolve material ambiguity before coding.
015. Examine critical assumptions.
016. Test business intent, not just implementation.
017. Evaluate realistic production scenarios.
018. Inspect infrastructure before adding dependencies.
019. Context precedes implementation.
020. Reuse appropriate existing components.
021. Define business entity identity explicitly.
022. Account for retries and duplicates.
023. Treat observability as a requirement.
024. Upfront planning can prevent costly failures.
025. Same tool can yield different outcomes.
026. Invest in specifications before implementation.
027. Prefer approved libraries and infrastructure.
028. Communicate organizational conventions.
029. Review against the specification.
030. Update specs when new requirements emerge.
031. Iterate specification, implementation and verification.
032. Optimize total delivery cost, not time to first code.
033. Practices apply to all software types.
034. Master transferable practices rather than products.
035. Treat AI platforms as replaceable tools.
036. Judgment matters as implementation gets easier.
037. Optimize allocation of attention, not personally written lines.
038. Develop specification literacy.
039. Develop verification discipline.
040. Own risks.
041. Understand the whole system.
042. Adopt practices incrementally starting with biggest gap.

## Derived skill candidates (not finalized)
- pre-implementation-analysis: business intent, architecture, reusable components, dependencies, edge cases, security, observability, acceptance criteria, assumptions.
- spec-driven-development: maintain evolving spec, implement, test, review against it; update spec when gaps emerge.
- architecture-guard: boundaries, consistency, dependency review, future maintainability.
- engineering-verification: independent checks, realistic cases, business acceptance, evidence and residual risk.
- context-engineering: explicit conventions, source hierarchy, relevant context, uncertainty.
- engineering-lifecycle: proportionate planning, implementation, verification, approvals and ownership.

## Original specification template
Business intent; functional requirements; existing architecture; reusable components; constraints; edge cases (retries, failures, duplicates, concurrency, missing data); observability; measurable acceptance criteria; testing strategy; deployment and rollback; open questions and assumptions; specification revisions.

## Repository plan
README.md, AGENTS.md, CLAUDE.md, PROGRESS.md, CHANGELOG.md; books/ai-native-software-engineering/chapter-01/ (notes, principles, applications, skill candidates); frameworks/; workflows/; templates/; skills/; prompts/; cheat-sheets/. Add later chapters only as provided. Keep canonical skills platform-neutral; separate optional installation for Claude Code and Codex. Keep instructions short and load relevant files on demand.

## Maintenance rules
At session start inspect AGENTS.md, PROGRESS.md and relevant index/files. For each new reading note, identify source and section, summarize in original words, label author-supported concept vs personal preference vs AI recommendation vs assumption, deduplicate, track contradictions, update progress and changelog, report changes. Do not claim unseen chapters are covered. Do not store full copyrighted text or screenshots in the repo. Keep company-specific details, credentials and proprietary data out of personal repo. Do not publish publicly. Keep skills as candidates until reviewed and tested; require approval before global installation or unrelated changes. Use git diff and review before commits/pushes; no force pushes. Suggested initial adoption: specs, context, verification, risk controls, then skills and orchestration. User likes handwritten diagrams and notes alongside digital implementation; use this as optional workflow preference.
