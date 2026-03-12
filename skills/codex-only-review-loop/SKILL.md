---
name: codex-only-review-loop
description: Pure Codex dual-role review loop (Reviewer + Author) without Claude MCP tooling. Use when user wants to run review-fix-rereview loop entirely inside Codex.
argument-hint: [topic-or-scope]
allowed-tools: Bash(*), Read, Grep, Glob, Write, Edit, Agent
---

# Codex-Only Review Loop

Run an autonomous review loop using only Codex in two explicit roles:
- `Reviewer`: scores work, identifies weaknesses, proposes minimum fixes
- `Author`: implements fixes, runs experiments, updates narrative

No external MCP reviewer is required.

## Context: $ARGUMENTS

## Constants

- MAX_ROUNDS = 4
- POSITIVE_THRESHOLD = score >= 6/10 and verdict in {"ready", "almost"}
- REVIEW_DOC = `AUTO_REVIEW_CODEX_ONLY.md`
- GPU_BUDGET_PER_ROUND = 4 GPU-hours (hard cap)

## Workflow

### Step 0: Initialize

1. Read project docs, paper draft, notes, and latest experiment outputs.
2. Create `AUTO_REVIEW_CODEX_ONLY.md` with run timestamp and scope.
3. Set `round = 1`.

### Step 1: Reviewer Pass

Use a strict reviewer prompt:

```text
Role: Reviewer (top-tier ML venue standard).
Task:
1) Score 1-10
2) Verdict: ready / almost / not ready
3) Ranked weaknesses (critical first)
4) Minimum fix for each weakness (experiment / analysis / reframing)
5) What evidence is required to change verdict in next round
Rules:
- Brutal honesty
- Do not optimize for kindness
- Penalize unsupported claims
```

Write the output to `AUTO_REVIEW_CODEX_ONLY.md`.

### Step 2: Stop Check

Stop if:
- score >= POSITIVE_THRESHOLD, and
- verdict is `ready` or `almost`.

If stopping, write final summary and remaining risks.

### Step 3: Author Pass (if not stopped)

For ranked fixes, implement highest impact first:

1. Patch code/analysis scripts.
2. Run feasible experiments.
3. If estimated cost > GPU_BUDGET_PER_ROUND, skip and mark `manual_followup`.
4. Prefer reframing or stronger analysis when it addresses the same weakness.
5. Record concrete evidence (metrics, tables, logs, failure cases).

### Step 4: Verify "Fix Before Re-Review"

Re-review is allowed only if all are present:
- code diff or doc diff,
- experiment/analysis outputs,
- round summary in `AUTO_REVIEW_CODEX_ONLY.md`.

### Step 5: Next Round

Increment `round` and repeat until max rounds.

If max rounds reached, produce:
- unresolved blockers,
- estimated cost to resolve each,
- recommendation: continue / pivot / submit to lower-risk venue.

## Hard Rules

- Never hide negative results.
- Never claim fixes without evidence.
- Keep claims aligned with actual experimental support.
- Prefer reproducibility over score gaming.

