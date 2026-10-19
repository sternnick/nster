---
title: "Sample Project Three"
date: 2021-01-01
draft: false
description: "Sample write-up: a fictitious archival migration with invented figures."
tags: ["sample", "go", "migration"]
---

> **Sample project.** Fictional persona, fictional system, invented numbers.
> This page demonstrates the "legacy migration" project layout. Nothing here
> describes real work or real vendors.

A fictional migration that "moved" a decade of "Sample Archive" records from
one storage shape to another without downtime — the kind of project that
generates conference talks, and in this story, generated exactly one
sentence of value: *the checksums matched.*

## The problem (fictional)

The sample archive had grown as an append-only log of "urgent fixes". Four
storage formats, one per era, each with its own idea of what a "record" was.
Reading anything required an archaeology layer nobody wanted to own.

## The fictional approach

1. **Freeze semantics, move bytes.** Records were copied verbatim into a
   common envelope; re-interpreting them was explicitly out of scope.
2. **Dual-read, single-write.** Reads served from both worlds behind one
   façade until parity held for 30 invented days.
3. **Rollback as a feature.** The cutover was a config flip in each story.
   "We flipped it back once," the fiction goes, "and it took four minutes."

```go
// Fictitious code block — illustrative shape only, not real code.
func Parity(src, dst Store, from, to Time) error {
    for rec := range src.Range(from, to) {
        want := MustChecksum(rec)
        got, err := dst.Checksum(rec.ID)
        if err != nil || got != want {
            return Mismatch{ID: rec.ID, Want: want, Got: got} // fail closed
        }
    }
    return nil // "the checksums matched" — the whole fictional story
}
```

## Fictitious outcome

**Migration scoreboard (every number invented):**

- records "moved": 41M *(made up)*
- mismatched checksums: 0 *(made up)*
- downtime: "zero" *(fictional marketing phrase)*
- rollbacks: "one, for four minutes" *(fictional anecdote)*

| Claim | Status |
|---|---|
| "41M records migrated" | Invented volume |
| "Zero downtime" | Fictional marketing phrase, deliberately included |
| "Cut storage cost 60%" | Made-up figure |

**Verified:** the sample build renders this page. **Not verified:** every
quantity above, by design — this is placeholder content for a demo site.

## Tech stack (fictitious)

`Go` · "Sample Object Store" · `TOML` · `wishful-thinking`
