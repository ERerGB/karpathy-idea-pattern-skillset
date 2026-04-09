---
name: ak
description: >-
  Top-level entry for the AK.skill pack: routes agent-era public-idea work to the right sub-skill (paradigm surface, proof, idea file, hype+discipline, irreducible core, scoreboard loop, year review).
  Use when the user invokes /ak, says AK.skill, or needs a single checklist for shipping a thread, README, talk, teaching repo, or annual stack essay without picking modules manually.
---

# AK.skill (entry)

You are guiding a **public technical idea** through a repeatable shape: compress the insight, prove it small, hand it off for agents, stay honest about limits. This file is the **router**; the other folders under this pack hold the checklists.

## First step

1. If the repo is checked out, read `doc/narrative-core.md` once for mission alignment (optional but fast).
2. Ask one clarifying question only if needed: **output shape** this week — *post/thread*, *long README*, *teaching artifact*, *experiment loop*, or *year-in-review essay*?

## Default pipeline (most common: post or thread)

Work **in order**, skipping steps that clearly do not apply:

| Order | Skill (`name`) | When to run |
| ----- | -------------- | ----------- |
| 1 | `paradigm-surface` | Always start here: lived delta + name the shift (+ optional metaphor / era). |
| 2 | `proof-in-miniature` | You claim a new capability or threshold → smallest runnable or linkable proof. |
| 3 | `hype-discipline-pairing` | Same narrative pass: limits + one verification habit + paradox / eval honesty if relevant. |
| 4 | `idea-file-handoff` | Only if attention spiked or people ask for “the repo”—promote pattern spec for agents. |

## Branch: teaching / minimal code artifact

- Lead with **`irreducible-core`** (single-file or gist + section tour; add commit-granular twin if the build is huge).
- Still use **`proof-in-miniature`** if you need a one-link falsifiable demo.
- Use **`hype-discipline-pairing`** when readers will ask “but does it work?”

## Branch: overnight agent experiments / optimization loop

- Use **`scoreboard-loop`** as the spine (metric + mutable surface + immutable prep).
- Pair with **`proof-in-miniature`** to publish the baseline artifact others can fork.

## Branch: annual or phase-change essay

- Use **`stack-year-review`** as the spine (stack t0/t1, notables, tensions, TL;DR).
- Pull **`paradigm-surface`** only if you need a new label for the year’s ontology shift.

## Anti-patterns

- Jumping to `idea-file-handoff` before there is a **named shift** and **one proof or honest limitation**.
- Running all seven every time—this entry skill exists to **trim** the path.

## Sub-skills (load on demand)

| `name` | Role |
| ------ | ---- |
| `paradigm-surface` | Surface + label the paradigm |
| `proof-in-miniature` | Claim + minimal proof |
| `idea-file-handoff` | Viral → agent-readable spec |
| `hype-discipline-pairing` | Hype welded to discipline |
| `irreducible-core` | Minimal teaching core |
| `scoreboard-loop` | Metric-driven iteration |
| `stack-year-review` | Year / phase longform |

**Repo:** https://github.com/ERerGB/AK.skill
