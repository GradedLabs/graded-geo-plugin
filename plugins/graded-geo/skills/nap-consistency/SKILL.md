---
name: nap-consistency
description: Find every place the site states its name, address and phone (NAP) and make them identical, including footer, contact page, JSON-LD, llms.txt and any embedded map. Use when asked "fix my NAP", "my address is different on some pages", or when a Graded report shows a fact mismatch between pages.
---

# NAP consistency

## Why it matters, honestly

AI answers that name a business usually repeat its name, address and phone from whatever page
or directory they read. If the site says three different things, the answer may say the wrong
one. Making the site agree with itself is the part we control. Whether an engine then picks the
right value is not measured here; say so.

## Find every occurrence

```bash
grep -rniE "<business name>|<street number> <street>|<phone digits with and without separators>" \
  --include=*.html --include=*.tsx --include=*.jsx --include=*.md --include=*.json --include=*.txt .
```

Also check: footer component, contact page, about page, JSON-LD blocks, `llms.txt`, `og:` tags,
email signatures in templates, embedded Google Maps `src`, and any `tel:` links.

## Pick the canonical form

Ask the owner for the one true form if there is any doubt. Then:

- Name: exactly as registered and as shown on the storefront (no "Inc." in one place and not another).
- Address: one format, USPS/postal style, same suite notation everywhere.
- Phone: one format for display (`(512) 555-0100`) and E.164 in `tel:` links and JSON-LD (`+15125550100`).

## Fix it at the source

If the site has a shared config or component, change it there and remove hard-coded copies.
If it does not, add one (`site.config.ts`, `_data/business.yml`, a CMS global) and point every
occurrence at it. One PR, titled "NAP: one source of truth".

## Verify

Re-run the grep: every hit is now the canonical form or reads from the shared source. Paste the
grep output (counts only, no customer data) in the PR.

## Say in the PR

"Aligns the business name, address and phone across N places and moves them to one source.
This makes the site agree with itself; it does not change what any directory or engine says
until they re-read the site."

## Receipt

Append a row to `.graded/runs/<date>/03_fix.md` — fix skill, branch, PR URL, rows targeted — and
stop until the owner merges or closes. Stage contract: `skills/03_fix/CONTEXT.md`.
