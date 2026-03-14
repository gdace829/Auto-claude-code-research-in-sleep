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
3. Provide either:
   - a seed PDF path/URL, or
   - a topic scope with keywords
4. Add any remaining scope you care about:
   - topic keywords
   - conference list
   - recency window (default: last 12 months)
   - max papers (default: 20)
5. Ask Codex to output using `REPORT_TEMPLATE.md` and save each run under `lit/`.
6. If a seed PDF is already provided, Codex should run immediately and infer missing scope from the seed.

## Output Location

- Default report directory: `lit/`
- English report pattern: `lit/LIT_REPORT_CODEX_ONLY_YYYYMMDD_HHMMSS.md`
- Chinese report pattern: `lit/LIT_REPORT_CODEX_ONLY_YYYYMMDD_HHMMSS_CN.md`
- Create `lit/` first if it does not already exist
