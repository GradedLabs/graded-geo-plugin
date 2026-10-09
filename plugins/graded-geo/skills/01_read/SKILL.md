---
name: 01_read
description: Stage 1 of the Graded GEO walk. Reads a website the way a plain fetch does — the page without JavaScript, robots.txt, llms.txt, JSON-LD, and whether the page links to its fact file — using the free Graded MCP tools, and records the rows verbatim. Use when starting a GEO fix run, when asked "what can AI read on my site", or before any fix.
---

# 01_read — see the site the way a plain fetch sees it

Contract: `CONTEXT.md` beside this file. Load nothing else from the plugin.

## Steps

1. **Open the run folder.** If `.graded/runs/<today>/` does not exist in the repository, copy
   `${CLAUDE_PLUGIN_ROOT}/_templates/run/` to `.graded/runs/<YYYY-MM-DD>/`.
2. **Ask two questions**, nothing more: the homepage URL, and the one page that should answer a
   customer's question (a services page, a location page, the page the owner cares about).
3. **Run the two free tools on both URLs**: `check_ai_crawl_access`, then `retrieval_gate_checklist`
   (MCP servers `graded-crawl-checker` and `graded-readiness` from `.mcp.json`). If the tools are not
   connected, open <https://usegraded.com/tools>, run the same checks there and paste the rows.
4. **Find the sources in the repository**, paths only: robots (`public/robots.txt`, `app/robots.ts`,
   or a CMS setting), the sitemap, `llms.txt`, the head template, the footer template, any JSON-LD,
   and where the business name, address and phone appear — count the places and the distinct forms,
   do not copy the values.
5. **Fill `01_read.md`** from the template. Copy each tool row exactly as printed. Where a tool says
   "could not tell", "could not run", or a bot wall refused the fetch, write `unmeasured` — never `0`,
   never `FAIL`.
6. Set the last line to `Done: yes` and stop. The next stage is `02_diagnose`.

## Rules

- Facts only. No fixes, no opinions, no ordering yet.
- Never guess what a crawler sees. Never call a paid probe. Never ask an engine anything.
