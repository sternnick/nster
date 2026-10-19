---
title: "Why a Static Site Is Still the Right Call for a CV"
date: 2024-11-02
draft: false
description: "Sample note: static generation vs hosted resume builders (fictitious content)."
tags: ["sample", "static-sites", "hugo"]
---

> **Sample note.** This is fictitious placeholder writing for a demo persona
> ("Jane Sample"). Nothing here describes a real person, employer, or product.

A CV is a document that happens to live on the web — it does not need a server,
a database, or an account with a resume platform. A static generator plus a
git repository covers everything a professional page actually requires.

## The three jobs of a CV site

1. **Render text reliably.** Markdown in, HTML out. Deterministic, every time.
2. **Stay available.** No runtime to crash; the page is a file on a CDN.
3. **Stay honest.** The cheapest failure mode of a personal site is drift —
   a "current role" that was true in 2022. Git history makes drift visible.

## What a CMS buys you (nothing)

An "edit from your phone" CMS is the usual sales pitch. For a document that
changes a handful of times per year, that convenience is outweighed by
another login, another attack surface, and another thing that quietly breaks.
A commit and a CI run is already six seconds from laptop to live page.

**Fictitious benchmark, made-up numbers:** rebuild time for the sample site
is "0.4 seconds", deploy is "90 seconds", and neither was measured against
anything real. Treat both figures as decoration.

## Where it gets interesting

The moment the pipeline is deterministic, you can hang audits on it — link
checkers, privacy gates, PDF generation. The site stops being a folder of
HTML and starts being a build target. That is the actual argument for static:
not speed, not cost, but *verifiability*.

---

*Placeholder note. Real-world numbers, links, and claims will appear only in
owner-approved content.*
