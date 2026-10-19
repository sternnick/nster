# ADR-002: Pin Hugo to 0.167.0

Status: accepted, **with one claim from the original note corrected**
Date: 2026-10-19

The same incorrect claim also lived in `hugo.toml` (since the v2 merge); it is
corrected alongside ADR-004.

## Context

The deploy workflow installs an explicitly pinned Hugo. When this decision was
taken, `main` pinned `0.168.0` and the v2 branch pinned `0.167.0`; since the v2
merge (`051a4d7`) main carries `0.167.0` too, so the two pins are one value. A
comment left in the workflow stated the reason as
*"blowfish v3.9.0 declares hugoVersion max=0.167.0 and hard-fails the build on
0.168.0 (verified 2026-10-19)"*.

That reason could not be reproduced from the theme, so it is recorded here as
unverified rather than repeated as fact:

- `theme.toml` at tag `v3.9.0` contains **no `[hugoVersion]` block**.
- `config/_default/module.toml` at the same tag is a **zero-byte blob**
  (`sha e69de29bb2d1d6434b8b29ae775ad8c2e48c5391`, `size 0`) — the other place
  Hugo would read a constraint from.
- Blowfish's own `hugo-version-update.yml` workflow pulls
  `gohugoio/hugo/releases/latest` and opens a PR to bump its config, i.e. the
  upstream policy is "track latest", not "cap at 0.167".
- Upstream does advertise a **minimum**: the `v3.9.0` README carries a
  `min-HUGO-version 0.162.0` badge. That is prose in a badge, not a constraint
  Hugo reads, so it does not change the analysis above — but it is where
  `README.md`'s "`>= 0.162.0`" comes from, and it is a real citation, not an
  invention.

## Decision

Keep the pin at **0.167.0**, on the basis that is actually evidenced: this site
builds green with it (run `39285257717`, "Build site" step succeeded on
`0.167.0` with Blowfish `v3.9.0`). Do **not** record `0.168.0` as known-bad —
with Blowfish it is simply **untested here**; the `0.168.0` that is proven in this
repository is the one `main` uses with the v1 theme.

## Consequences

- `main` and `v2-multipage` intentionally run different Hugo versions until the
  merge; a version bump must then be reconciled in one place.
- Upgrading is a deliberate, reviewable commit — never a floating `latest`, which
  would let an upstream Hugo release break the deployment silently.
- Open item: run one build of this site at `0.168.0` to turn "untested" into a
  measured result. Until then the pin stands on the green run, not on a claim.

## Evidence

`theme.toml` and `config/_default/module.toml` at `v3.9.0` via the contents API;
`.github/workflows/hugo-version-update.yml` in `nunocoracao/blowfish@v3.9.0`;
run `39285257717`; `git show main:.github/workflows/hugo.yaml | grep HUGO_VERSION`.
