---
title: "Sample Project Two"
date: 2022-01-01
draft: false
description: "Sample write-up: a fictitious internal tool with invented metrics."
tags: ["sample", "typescript", "tooling"]
---

> **Sample project.** Every name, number, and outcome here is invented for
> the demo persona ("Jane Sample"). This page exists to show project-page
> layout, not to describe real work.

A fictional internal web tool that "gave" a sample operations team a single
screen for the status of "Sample Services" — because in this story, nobody
could remember which of the eleven dashboards was current.

## The problem (fictional)

Eleven dashboards, zero trust. The fictional team kept a *twelfth* artifact:
a shared document titled "what's actually down", manually edited. The tool's
entire job was to make that document obsolete.

## Design choices (fictional, with fake trade-offs)

- **One endpoint, one page.** No websocket theater; the page "polled" every
  10 s. (Invented design claim.)
- **History over prediction.** The UI answered "what happened at 03:00", not
  "what might happen". (Fictional product philosophy.)
- **Degrade ugly.** If a probe failed, the tile showed "UNKNOWN" instead of
  green. False green was banned as the tool's one cardinal sin.

```ts
// Fictitious code block — illustrative shape only, not from any real codebase.
type Tile = { name: string; state: "ok" | "down" | "unknown" };

function worst(tiles: Tile[]): Tile["state"] {
  if (tiles.some((t) => t.state === "down")) return "down";
  if (tiles.some((t) => t.state === "unknown")) return "unknown";
  return "ok"; // "unknown" can NEVER render as ok — fictional invariant
}
```

## Fictitious outcome

| Service (fake name) | State (fake) |
|---|---|
| service-a | ok |
| service-b | **down** |
| service-c | UNKNOWN |

*Fake status board — sample data only, no real service named or measured. The
gray "UNKNOWN" tile is the joke of the design: unknown is its own color.*

| Claim | Status |
|---|---|
| "Took 6 weeks to ship" | Invented timeline |
| "p95 latency under 200 ms" | Made-up performance number, never measured |
| "Reduced incident confusion 40%" | Fictional outcome metric |

**Verified:** this page builds and renders. **Not verified:** anything the
page asserts about the fictional tool — because the tool isn't real.

## Tech stack (fictitious)

`TypeScript` · `htmx` · "Sample Cloud Two" · "Probe Lite OSS"
