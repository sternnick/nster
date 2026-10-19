# nster — personal site (Hugo + GitHub Pages)

Hugo static site published to GitHub Pages via GitHub Actions.

**Status: SAMPLE ONLY.** Every name, employer, project, date, and contact value on
the site is fictitious placeholder content. Real content will be added only after
separate owner approval.

- Theme: [Blowfish](https://github.com/nunocoracao/blowfish) v3.9.0 as a git
  submodule (MIT), pinned to the exact tag.
- Hugo: pinned `0.167.0` extended in CI (Blowfish v3.9.0 declares
  `hugoVersion max = 0.167.0`; verified at pin time).
- PDF: `.github/workflows/hugo.yaml` renders `public/cv.pdf` from the built CV
  page with pinned Chrome for Testing and publishes it at `/nster/cv.pdf`.
  The PDF is a build artifact — never committed to git.
- CI: `.github/workflows/hugo.yaml` (build + deploy) and `pr-gate.yml`
  (strict build, privacy gate, PDF text audit).
- Config: `hugo.toml`, `baseURL = https://sternnick.github.io/nster/`
- Content lives in `content/` as markdown page bundles:

```
content/
├── _index.md                      # home
├── cv/index.md                    # /cv/
├── projects/                      # /projects/ (auto list page)
│   └── sample-project-*/index.md
└── about/index.md                 # /about/
```

## Local build

Requires Hugo extended >= 0.162.0 (0.167.x matches CI).

```bash
git submodule update --init --recursive
hugo --gc --minify --panicOnWarning
```

## Theme updates

Bump the submodule to a new tag, rebuild, merge via PR:

```bash
git -C themes/blowfish checkout v<x.y.z>
git add themes/blowfish
```

## Deployment

Pages source = GitHub Actions (set once in Settings → Pages). The deploy job
publishes via `actions/deploy-pages`. Rollback: revert the merge commit; the
build-gated pipeline redeploys the previous state.
