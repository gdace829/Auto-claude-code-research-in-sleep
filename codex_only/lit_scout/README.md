# Codex-Only Literature Scout

Pure Codex workflow for collecting the most worthwhile *recent* top-tier papers and generating a structured report.

- No Claude Code skill command required
- Single Codex session
- Deterministic output format for easy comparison across runs

## Files

- `LOOP_PROMPT.md`: paste as your first prompt in Codex
- `REPORT_TEMPLATE.md`: required output structure

## Quick Start

1. Open Codex in your research repo.
2. Paste `LOOP_PROMPT.md` into the first prompt.
3. Fill your scope:
   - topic keywords
   - conference list
   - recency window (default: last 12 months)
   - max papers (default: 20)
4. Ask Codex to output using `REPORT_TEMPLATE.md`.
5. Save as `LIT_REPORT_CODEX_ONLY.md`.

