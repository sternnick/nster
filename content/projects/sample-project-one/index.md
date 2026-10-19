---
title: "Sample Project One"
date: 2023-01-01
draft: false
description: "Sample write-up: a fictitious data pipeline with made-up numbers."
tags: ["sample", "python", "data"]
---

> **Sample project.** Fictitious persona, fictitious tooling, invented
> metrics. Nothing on this page describes real work. All figures below are
> deliberately made up and marked as such.

A fictitious batch pipeline that "moved" sample records from Sample Source A
to Sample Warehouse B nightly. Presented here only to show what a real
project write-up would look like on this site.

## The problem (fictional)

The sample department exported "nightly extracts" as CSV dumps. Every month a
"dump" was late, duplicated, or silently truncated. No one could answer, for
any given day, whether the warehouse matched the source.

## What the fictional system did

```python
# Fictitious code block — illustrative shape only, not runnable,
# not from any real project.
def reconcile(day: str) -> Diff:
    src = source.read(day)          # "Sample Source A" (made up)
    dst = warehouse.read(day)       # "Sample Warehouse B" (made up)
    return Diff(
        missing=src.keys() - dst.keys(),
        extra=dst.keys() - src.keys(),
        checksum_mismatch=[k for k in src & dst
                           if src[k].crc != dst[k].crc],
    )
```

Every run produced a one-page diff report. Boring by design: the point was
never cleverness, it was that anyone could open the report and stop arguing.

## Fictitious outcome

{{< figure src="/img/sample-architecture.jpg" alt="Invented four-box architecture diagram of the fictitious pipeline: Sample Source, Sample API, Sample Store, Sample Cache, annotated with RFC 5737 documentation IPs" caption="The fictitious system's made-up topology. The IP addresses are RFC 5737 documentation examples — they route nowhere." >}}

| Month (fake) | Incident count (fake) |
|---|---|
| M1 | 41 |
| M2 | 29 |
| M3+ | 12 |

*Every number in this table is invented for layout. No real measurement took
place.*

| Claim | Status |
|---|---|
| "Incidents dropped 70%" | **Made-up sample number** — never measured |
| "Reconciles 4M rows nightly" | Invented capacity figure |
| "Adopted by 3 teams" | Fictional adoption |

**Verified:** the sample build runs and renders this page.
**Not verified:** everything else on this page — it is placeholder text for a
demo persona.

## Tech stack (fictitious)

`Python` · `Docker` · "Sample Warehouse B" · "Scheduler Pro Enterprise"
