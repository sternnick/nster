---
title: "About this site"
description: "How this site is built and deployed"
---

This site is a static Hugo website hosted on GitHub Pages.

- **Content** lives in markdown files in the repository; nothing is edited by
  hand after the build.
- **Build**: [Hugo](https://gohugo.io/) with a pinned version, run by GitHub
  Actions on every change. A broken internal link or build warning fails the
  build instead of shipping.
- **Theme**: [Blowfish](https://github.com/nunocoracao/blowfish) as a git
  submodule pinned to an exact version tag; updates arrive as dependency pull
  requests.
- **Deploy**: the workflow publishes the built site with
  `actions/deploy-pages`; a PDF version of the CV is rendered from the same
  build by headless Chromium and published alongside it.
- **Print**: the CV page is styled for printing directly from the browser.

The current content is placeholder samples only.
Contact: test.person@reserved.test or +353-123456789
