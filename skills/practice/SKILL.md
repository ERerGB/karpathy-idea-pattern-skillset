---
name: practice
description: Use when the user wants to iteratively improve copy, product language, prompts, CTAs, landing page text, launch posts, or narrative through repeated generation, submission, review, and revision. Supports configurable provider/model/language routing such as using DeepSeek-V4 through API Proxy for Chinese copy polishing.
---

# Practice

Practice is a controlled iteration loop for improving text.

Use it for:
- product copy
- CTAs
- landing page sections
- prompts
- emails
- launch posts
- brand narrative
- bilingual copy

The core loop is:

1. Define brief
2. Generate candidate
3. Submit candidate
4. Review submission
5. Revise
6. Stop when configured conditions are met

## Configuration

At the start, infer a config from the user request. Ask only when a missing value would materially change the result.

Default config:

```yaml
practice:
  task: copy_polish
  language: auto
  audience: inferred
  provider: default
  model: default
  max_rounds: 3
  stop_mode: self_revision_pass
  review_threshold: 31
  preserve_meaning: true
  avoid_overclaim: true
  output_mode: best_only
```

When the user specifies a provider, model, language, or source, use that routing.

Example routing:

```yaml
practice:
  provider: api_proxy
  endpoint: /proxy/openai/v1/chat/completions
  model: deepseek-v4
  language: zh
  purpose: copy_polish
```

Do not expose secrets. Do not print bearer tokens, JWTs, API keys, or full environment files.

If a requested model is unavailable, report it clearly. Do not silently substitute another model unless the user allows fallback.

## Brief

Create a brief before the first candidate.

```yaml
brief:
  goal:
  audience:
  scene:
  language:
  must_keep:
  must_avoid:
  tone:
  success_criteria:
```

If the user provides enough context, infer the brief and proceed.

## Submission Format

Each round creates a submission:

```md
## Submission 001

### Candidate
...

### Intent
...

### Changes From Previous
...

### Known Tradeoffs
...
```

## Review Rubric

Score each dimension from 1 to 5:

```yaml
rubric:
  user_clarity:
  product_truth:
  scene_fit:
  content_craft:
  repetition_control:
  action_pull:
  language_surface:
```

Maximum score: 35.

Reviewer output must include:
- total score
- top 1-3 issues
- exact revision instruction for the next round
- pass/fail

## Stop Conditions

Stop when any configured stop condition is met.

Supported stop modes:

```yaml
stop_mode:
  fixed_rounds
  self_revision_pass
  threshold
  plateau
```

Default pass rule:

```yaml
pass_if:
  total_score_gte: 31
  no_dimension_below: 4
  no_blocking_issue: true
```

For `fixed_rounds`, stop after `max_rounds`.

For `threshold`, stop when total score reaches `review_threshold`.

For `plateau`, stop when score does not improve for 2 consecutive rounds.

## Iteration Rules

- Generate one candidate per round unless branching is explicitly useful.
- Each round should make the smallest useful revision.
- Preserve product truth over elegance.
- Prefer concrete user-facing language.
- Reduce weak repeated nouns and filler abstractions.
- Track what changed between rounds.
- Stop when the configured condition is met.

## Output Modes

```yaml
output_mode:
  best_only
  full_trace
  diff
  recommendation
```

Default: `best_only`.

Use `full_trace` when the user wants to inspect all rounds.

Do not expose private chain-of-thought. Provide structured trace only: candidate, score, issues, revision instruction, and stop reason.
