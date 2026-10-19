---
title: "About this site"
description: "How this site is built and deployed"
---

This site is a static Hugo website hosted on GitHub Pages.

- **Content** lives in markdown files in the repository; nothing is edited by
  hand after the build.
- **Build**: [Hugo](https://gohugo.io/) with a pinned version (extended
  build, `0.167.0`), run by GitHub Actions on every change. A broken internal
  link or build warning fails the build instead of shipping. CI also runs
  content-hygiene audits (sample-email allowlist, phone-pattern scan) over
  the tree and over the generated PDF before anything is published.
- **Theme**: [Blowfish](https://github.com/nunocoracao/blowfish) as a git
  submodule pinned to an exact version tag; updates arrive as dependency pull
  requests. Project-specific tweaks live in `assets/css/custom.css`, which
  loads after the theme styles — the submodule itself is never edited.
- **Deploy**: the workflow publishes the built site with
  `actions/deploy-pages`; a PDF version of the CV is rendered from the same
  build by pinned Chrome for Testing and published alongside it.
- **Print**: the CV page is styled for printing directly from the browser.

The current content is placeholder samples only.
