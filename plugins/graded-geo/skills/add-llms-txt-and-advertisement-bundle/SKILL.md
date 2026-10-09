---
name: add-llms-txt-and-advertisement-bundle
description: Add /llms.txt built from the sitemap, plus the visible advertisement bundle (footer link, <link rel="alternate">, a line in robots.txt) so agents can find it without hidden text. Use when asked "add llms.txt", "make an llms.txt", "how do I publish llms.txt", or after a checklist reports llms.txt missing.
---

# Add llms.txt and advertise it honestly

## What llms.txt is, in one line

A plain-text index at `/llms.txt`: a title, one summary line, and a list of the pages that
matter, each with a one-line note. It gives an agent your facts if it fetches the file.
Google says it does not use these files. Other engines have not said either way. It carries
no score weight. Say exactly that in the PR; nothing more.

## Build the file

1. Generate it from the sitemap: `generate_llms_txt` (MCP) or
   <https://usegraded.com/tools/llms-txt>. Up to 50 pages, titles from paths.
2. Edit the titles and notes by hand from the real page content. The note is the one sentence
   a reader needs: what the page answers, not marketing copy.
3. Keep it short. The spec shape: `# Site name`, `> one summary line`, `## Pages` list, optional
   `## Optional` list. See <https://llmstxt.org/>.

## Publish it

- Static site: `public/llms.txt`.
- Next.js App Router: `app/llms.txt/route.ts` returning `text/plain; charset=utf-8`, built
  from the same page list the sitemap uses so they cannot drift.
- CMS: a plain-text page at `/llms.txt`, no HTML wrapper.

## Advertise it — visibly, never hidden

1. Footer, on every page: one visible sentence with the link — "Reading this with an AI assistant?
   Our facts for AI tools" or "For AI agents: llms.txt" — normal size, real contrast, selectable.
   The sentence is the disclosure; the link is the pointer.
2. Head: `<link rel="alternate" type="text/plain" href="/llms.txt" title="llms.txt">`.
3. robots.txt: a comment line `# llms.txt: https://example.com/llms.txt` under the Sitemap line.
4. Sitemap: a URL entry for `/llms.txt` where the sitemap is yours to edit. The free tools do not
   read the sitemap; say so in the PR rather than ticking it.

No hidden text, no white-on-white, no `display:none` blocks. If the owner asks for a hidden
link, refuse and explain that hidden text can get a site penalised.

## Verify

`retrieval_gate_checklist` (MCP) or <https://usegraded.com/tools/llm-optimizer>: the llms.txt
row reads "found" and, once the page is live, the "Page points to llms.txt" row reads "yes — a
visible link on the page" (stage `04_advertise` records the before and after). Fetch `/llms.txt`
with curl and paste the first ten lines in the PR.

## Say in the PR

"Adds /llms.txt (an index for AI agents) and links it visibly from the footer and page head.
This file has zero score weight and no measured effect on rankings; it exists so an agent that
fetches it gets our facts instead of guessing."

## Receipt

Append a row to `.graded/runs/<date>/03_fix.md` — fix skill, branch, PR URL, rows targeted — and
stop until the owner merges or closes. Stage contract: `skills/03_fix/CONTEXT.md`.
