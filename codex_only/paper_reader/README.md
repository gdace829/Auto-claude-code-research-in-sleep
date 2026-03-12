# Codex-Only Paper Reader

Pure Codex workflow for deep reading of a single paper and producing an action-oriented summary.
It also supports reading a `lit_scout` report, downloading linked PDFs into `papers/`, and then reading selected papers.

## Files

- `LOOP_PROMPT.md`: paste into Codex as the first prompt
- `REPORT_TEMPLATE.md`: required output structure

## Quick Start

1. Open Codex in your project directory.
2. Paste `LOOP_PROMPT.md` into the first prompt.
3. Provide one paper input:
   - local PDF path, or
   - arXiv/OpenReview/ACL URL
   - OR one `lit_scout` report path (markdown with links)
4. Input priority:
   - If explicit PDF/URL is provided, read that paper.
   - If explicit local PDF path is missing, search online and try to download it first.
   - Only if explicit input is absent or online download fails, fallback to `lit_scout` top papers.
5. Optional: choose paper ranks when using `lit_scout` input (default top 3).
6. Require output with `REPORT_TEMPLATE.md`.
7. Save outputs to timestamped files:
   - `PAPER_READING_YYYYMMDD_HHMMSS.md`
   - `PAPER_READING_YYYYMMDD_HHMMSS_CN.md`
   - `PAPER_DOWNLOAD_LOG_YYYYMMDD_HHMMSS.md`
