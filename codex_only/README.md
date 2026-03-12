# Codex-Only Workflows

Pure Codex workflows without Claude Code skill commands.

## Folder Structure

- `review_loop/`: iterative review -> fix -> re-review
- `lit_scout/`: collect recent top-venue papers and generate a structured report
- `paper_reader/`: deeply read one paper and produce execution-ready notes

## Review Loop Quick Start

1. Open `review_loop/LOOP_PROMPT.md`.
2. Paste it into Codex as the first prompt.
3. Use `review_loop/ROUND_TEMPLATE.md` for round outputs.
4. Save to `AUTO_REVIEW_CODEX_ONLY.md`.

## Literature Scout Quick Start

1. Open `lit_scout/README.md`.
2. Paste `lit_scout/LOOP_PROMPT.md` into Codex as first prompt.
3. Require output with `lit_scout/REPORT_TEMPLATE.md`.
4. Save to `LIT_REPORT_CODEX_ONLY.md`.

## Paper Reader Quick Start

1. Open `paper_reader/README.md`.
2. Paste `paper_reader/LOOP_PROMPT.md` into Codex as first prompt.
3. Provide one paper input (PDF path or URL).
4. Require output with `paper_reader/REPORT_TEMPLATE.md`.
