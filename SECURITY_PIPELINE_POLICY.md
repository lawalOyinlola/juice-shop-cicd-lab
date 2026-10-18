# Security pipeline policy

## What blocks a merge
- Any unsuppressed secret in the full git history.
- ERROR-severity static analysis findings, and HIGH or CRITICAL on Semgrep's newer scale.
- CRITICAL dependency vulnerabilities with a published fix.

## What warns
Everything else, including all upstream image findings.

## Every finding gets exactly one outcome
- Fixed: link the commit.
- Accepted: a technical reason and a review date. No date, no acceptance.
- False positive: the reasoning, stated, so the next reviewer does not redo it.

## Triage log
| Finding | Decision | Reason | Decided | Review |
|---|---|---|---|---|
| 225 secrets in full git history | Accepted | Juice Shop's secrets are deliberate training material, accepted as a batch for this stand-in run | 2026-10-18 | 2027-01-18 |
| 7 CRITICAL dependency CVEs with a fix | Accepted | Deliberately vulnerable training app, accepted as a batch with expiry dates in security/.trivyignore | 2026-10-18 | 2027-01-18 |
| 29 ERROR static analysis findings | Accepted | Deliberate training vulnerabilities, files listed in .semgrepignore | 2026-10-18 | 2027-01-18 |
