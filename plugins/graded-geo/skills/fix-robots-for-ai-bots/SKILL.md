---
name: fix-robots-for-ai-bots
description: Edit robots.txt so the named AI crawlers (GPTBot, OAI-SearchBot, ChatGPT-User, ClaudeBot, Claude-SearchBot, PerplexityBot, Perplexity-User, Google-Extended, Bingbot and the rest) are allowed or deliberately blocked, with a readable diff. Use after a crawl check reports a bot blocked, or when asked "fix robots for AI bots", "allow GPTBot", "block AI crawlers".
---

# Fix robots.txt for AI bots

## Check first

Run the Graded crawl check on the homepage and one deep page:
`check_ai_crawl_access` (MCP) or <https://usegraded.com/tools/ai-crawl-checker>. Note the
"robots.txt" row: which named bots are blocked. A missing robots.txt allows everyone — that is
not a failure, do not add a file just to have one.

## Decide with the owner

Ask one question: "Do you want AI assistants to be able to read and cite this site?" Yes is
the normal answer for a business site. No is legitimate (some publishers) — then block on
purpose and say so in the PR.

## Make the change

Find the file (`public/robots.txt`, `static/robots.txt`, `app/robots.ts` in Next.js, a CMS
setting). Preserve every existing rule. Add one group per bot you are changing, grouped by
intent:

```
# AI assistants — retrieval and on-demand fetch (answers that cite you)
User-agent: OAI-SearchBot
User-agent: ChatGPT-User
User-agent: Claude-SearchBot
User-agent: Claude-User
User-agent: PerplexityBot
User-agent: Perplexity-User
Allow: /

# AI training crawlers — allow or block separately; this is a separate decision
User-agent: GPTBot
User-agent: ClaudeBot
User-agent: Google-Extended
Allow: /
```

Keep `Disallow` lines for admin, cart, search-result and private paths. Do not remove a
`Sitemap:` line; add one if the sitemap exists and it is missing.

## Verify

Re-run the crawl check. The robots row should now list the bots you intended. Put the before
and after rows in the PR description.

## Say in the PR

"Allows the named AI crawlers to read public pages. This changes what a plain fetch is
permitted to read; it does not change what any assistant answers, and we have not measured
that here."

## Receipt

Append a row to `.graded/runs/<date>/03_fix.md` — fix skill, branch, PR URL, rows targeted — and
stop until the owner merges or closes. Stage contract: `skills/03_fix/CONTEXT.md`.
