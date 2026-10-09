---
name: answer-block-and-faq
description: Put a short, direct answer about the business near the top of a page (who you are, where, what you do, for whom) and a real FAQ below it, in the page's own words. Use when the readiness checklist reports "answer block: not found", or when asked "make my page answer-ready", "add an answer block", "add an FAQ for AI".
---

# Answer block and FAQ

## Why this row exists

Most AI fetchers read the first few hundred words of server-rendered text. If the first
paragraph is a slogan, the fetcher leaves with no facts. The answer block is two to four plain
sentences that say what the business is, where it works, what it does, and for whom — in the
HTML, not injected by JavaScript.

## Check first

Run `retrieval_gate_checklist` (MCP) or <https://usegraded.com/tools/llm-optimizer>. Note the
"Answer block" and "Enough text without JavaScript" rows. If the text row fails, the page is
rendered client-side; fix that first (server-render or static-export the page) or the answer
block will not be read either.

## Write the block

- Place it directly under the H1, before any carousel or hero image copy.
- Use the business name as written elsewhere on the site.
- Two to four sentences. Example shape: "Acme Plumbing is a licensed plumber in Austin, Texas.
  We handle emergency repairs, water heaters and repiping for homeowners in Travis County.
  Call (512) 555-0100, 24 hours."
- Every fact must already appear on the site or be confirmed by the owner. Do not add
  "best", "top-rated" or any claim the page does not back.

## Write the FAQ

- Five to eight questions customers actually ask, each answered in one or two sentences.
- Real HTML (`<h2>`/`<h3>` + `<p>`, or `<details>`), server-rendered. A FAQ hidden behind a
  JavaScript accordion that renders empty without JS does not count.
- If the site already has FAQ JSON-LD, make sure the visible text matches it word for word.

## Verify

Re-run the checklist. The answer block row should read PASS; the word count should rise. Put
both rows, before and after, in the PR.

## Say in the PR

"Adds a plain-language answer block under the H1 and a visible FAQ. This makes the page's facts
readable to a plain fetch. It does not promise any engine will quote them."

## Receipt

Append a row to `.graded/runs/<date>/03_fix.md` — fix skill, branch, PR URL, rows targeted — and
stop until the owner merges or closes. Stage contract: `skills/03_fix/CONTEXT.md`.
