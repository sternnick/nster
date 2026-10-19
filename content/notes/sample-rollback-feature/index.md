---
title: "Rollback Is a Feature: Undo Paths for Non-Software Teams"
date: 2025-02-08
draft: false
description: "Sample note: designing reversible decisions (fictitious content)."
tags: ["sample", "process", "reliability"]
---

> [!NOTE]
> Fictitious placeholder writing for the demo persona. The
> "team", "system", and every number below are invented.

Every team believes it wants speed. Fewer teams want the thing that actually
makes speed possible: the ability to take a change *back* in under five
minutes, without an argument and without a hero.

## The undo budget

A fictional rule of thumb: a decision is cheap if undoing it costs less than
a coffee break. Most "strategic" debates are really disagreements about undo
cost — two people agreeing on the goal and disagreeing about whether step
four is reversible. Write the undo path down and half the argument dissolves.

| Change (fictional) | Undo cost (made up) | Verdict |
|---|---|---|
| Copy a config file | seconds | just do it |
| Rename a shared field | "half a day, allegedly" | schedule it |
| Delete the old dashboard | "one afternoon of regret" | gate it |

*Timings invented. No team of eleven was consulted in the making of this
table.*

## What makes undo fail

1. **The irreversible step hides mid-sequence.** A "reversible" migration
   becomes permanent at the one line where old data is truncated. Find the
   truncation point; it is the whole design problem.
2. **Undo rots.** An untested rollback path is a rumor. The fictional team
   "flipped the switch back quarterly, at 10:00 on a Tuesday, in daylight."
3. **Social irreversibility.** The technical revert works; the twelve people
   who saw the broken state do not revert in their heads. Announce the undo
   as loudly as the change.

## The honest caveat

Some things genuinely are one-way doors, and pretending otherwise is how
sites (and careers) acquire incidents. The skill is sorting the two piles —
and defaulting every "probably reversible" claim to *unverified* until an
actual drill proves it.

---

*Placeholder note. The real version would cite an actual drill log, dates
included.*
