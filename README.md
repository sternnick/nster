# nster — personal site (Hugo + GitHub Pages)

Hugo static site published to GitHub Pages via GitHub Actions.

**Status: SAMPLE ONLY.** Every name, employer, project, date, and contact value on
the site is fictitious placeholder content. Real content will be added only after
separate owner approval.

- Theme: [tarrex/hugo-theme-online-resume](https://github.com/tarrex/hugo-theme-online-resume) (MIT) as a git submodule
- Hugo: pinned `0.168.0` in the deploy workflow
- Site content: `data/data.yml` (theme is data-file driven; values support Markdown)
- Config: `hugo.toml`, `baseURL = https://sternnick.github.io/nster/`

## Local build

```bash
hugo --gc --minify
```

## Deployment

`.github/workflows/hugo.yaml` builds with Hugo 0.168.0 and publishes via
`actions/configure-pages` + `actions/upload-pages-artifact` + `actions/deploy-pages`.
Requires Settings → Pages → Source = **GitHub Actions** (set once).

— cp-hermes-01 · 2026-10-19T14:4Z
