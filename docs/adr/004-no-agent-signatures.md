# ADR-004: No agent or tool signatures in shipped artifacts

Status: accepted
Date: 2026-10-19

## Context

The v2 merge (`051a4d7`, PR #1) appended an authoring-agent signature — an
internal agent handle plus an automation timestamp — to the end of `README.md` in
a **public** repository. It stayed reachable for roughly four hours until PR #13
removed it (`aeed386`).

It is not a secret, and nobody's personal data was exposed. What it leaked is
internal structure: that an automated agent authored the file, which agent, and
at what minute. That is a fact about our tooling, published in a product artifact
nobody intended it to be part of.

**Why the audit missed it.** The identifier patterns we run are
address/domain/key-shaped (`…@sterniotis.com`, phone shapes, `BEGIN … PRIVATE
KEY`, `ghp_…`). A bare agent handle, on its own, matches none of them.
The same class of miss applies to any internal username, hostname, or agent name
written without a domain attached.

## Decision

Nothing that ships — README, page content, code comments, commit messages, PR
titles/bodies in a public repo — carries an authoring-agent signature, an
automation timestamp styled as a signature, or an internal hostname/agent name.

Provenance belongs in commit metadata and in the PR discussion, where it is
attributable, reviewable, and not part of the product surface.

## Consequences

- The CI content-hygiene gate **keeps no identifier deny-list** (its own comment
  says so, and hardcoding one into a public repo publishes the very list an
  attacker wants). Detection of this class therefore stays **out-of-band** — and
  out-of-band currently means **ad hoc**: today's audits were grep patterns
  assembled by hand inside a session, and there is no maintained pattern file in
  the tooling. Until such a set exists and is versioned somewhere durable,
  nothing structurally catches a bare agent handle; it depends on whoever runs
  the audit remembering to include one. That is an open action, not a control.
- An authored-by line in generated prose is treated as a review defect, not a
  style nit: it is removed before merge, not after.
- The four-hour window is the reason this is an ADR and not just a reverted line:
  once public, text in a repo README is out there regardless of deletion.

## Evidence

`git log --oneline -- README.md`; the added line is visible in the v2 merge commit
and absent from `git show aeed386:README.md | tail -3`; removal in PR #13; the
gate's no-deny-list rule stated in `.github/workflows/hugo.yaml`. This ADR
intentionally does not quote the line — quoting it here would republish it.
