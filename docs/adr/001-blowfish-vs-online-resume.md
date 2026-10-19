# ADR-001: Blowfish instead of hugo-theme-online-resume

Status: accepted (implemented on branch `v2-multipage`; `main` still runs v1)
Date: 2026-10-19

## Context

v1 (`main` at `ae9b37f`) used `themes/hugo-theme-online-resume` as a submodule
(`tarrex/hugo-theme-online-resume`, gitlink `914afdb`). That theme is not a
multi-page theme at all: its `layouts/all.html` renders one page out of a single
data file (`{{ index hugo.Data $dataFile }}`), which is why v1 had **no `content/`
directory** and `hugo.toml` set `disableKinds = ['section','taxonomy','term','rss','sitemap','404']`.
Everything the site knew about itself lived in `data/data.yml`.

The requirement driving v2 is separate pages with their own URLs — Home, About,
CV, Projects — plus normal Hugo authoring (`archetypes/`, `hugo new`), which a
data-file theme cannot express.

## Decision

Replace the theme with **Blowfish** (`nunocoracao/blowfish`, submodule pinned to
tag `v3.9.0`, gitlink `ebe683e`), and move the site's substance into real content
files: `content/_index.md`, `content/about/index.md`, `content/cv/index.md`,
`content/projects/` (+ three sample projects), with `assets/css/custom.css` for
the small visual deviations from stock Blowfish.

## Consequences

- `data/data.yml` (136 lines) is deleted; content moves into markdown. The whole
  sample-vs-real distinction now lives in markdown, which is what the content
  hygiene audits in CI scan.
- The site gains per-page URLs, a real navigation, search and dark mode, at the
  cost of a Tailwind-based theme whose asset pipeline we do not control.
- The CV PDF artifact (ADR-003) now has a page to print, which v1 effectively
  did not have.
- Theme updates are submodule bumps, so they arrive as reviewable commits rather
  than silent upstream changes.

## Evidence

`git show --stat 0a51e73` (17 files, +355/−217), `.gitmodules` before/after,
`git show ae9b37f:themes/hugo-theme-online-resume` vs
`git show v2-multipage:themes/blowfish`.
