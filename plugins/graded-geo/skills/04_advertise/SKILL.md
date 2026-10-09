---
name: 04_advertise
description: Stage 4 of the Graded GEO walk, the reverse-mullet step. Makes the site's fact file (llms.txt) findable from the page a model is already reading — a visible footer link, a head link, a robots.txt line and a sitemap entry — with no hidden text, then verifies the "Page points to llms.txt" row with the free check. Use after an llms.txt exists, or when asked "nobody fetches my llms.txt" or "advertise my llms.txt".
---

# 04_advertise — say the file exists, where a model reads

Why this stage exists: a fact file nothing links to is rarely fetched. In the one published test, a
model fetched a site's llms.txt only after the page itself named the file — and that test used a
hidden 9px link we will not copy. We ship the visible version and measure it; we do not claim its
effect, and the file keeps zero score weight.

Contract: `CONTEXT.md` beside this file. The markup snippets live in one place —
`skills/add-llms-txt-and-advertisement-bundle/SKILL.md`, section "Advertise it — visibly, never
hidden". Read that section; do not restate it here.

## Steps

1. Branch `graded/advertise-llms-txt`.
2. **Footer link** on every page: normal size, real contrast, selectable, text that says what it is
   ("Our facts for AI tools" or "For AI agents: llms.txt"). The owner approves the wording.
3. **Head link**: `<link rel="alternate" type="text/plain" href="/llms.txt" title="llms.txt">`.
4. **robots.txt line** (`# llms.txt: https://example.com/llms.txt`, or an `Llms:` line) where the
   platform lets you edit robots.txt.
5. **Sitemap entry** for `/llms.txt` where the sitemap is yours to edit. The free tools do not read
   the sitemap, so that row stays blank in the receipt — say so, do not tick it.
6. **Tripwire before the PR.** Grep your diff for the new markup; any hit means stop and fix:
   `display:none`, `visibility:hidden`, `opacity:0`, `font-size:` under 10px, `user-select:none`,
   `aria-hidden`, `text-indent:-`, `left:-9999`, an empty link text. Then open the page in a
   browser: can a person see and click the link? If not, it is hidden, whatever the CSS says.
7. Open the PR with the paragraph below and the before "Page points to llms.txt" row from `01_read.md`.
8. After merge and deploy, run `check_ai_crawl_access` on the homepage: the row must read
   `yes — a visible link on the page (...)`. Paste before and after into `04_advertise.md`. `Done: yes`.

## Say in the PR

"Links the site's llms.txt visibly from the footer and the page head, and names it in robots.txt
and the sitemap. No hidden text. This makes the file findable from the page; whether any assistant
fetches it is not measured here, and the file carries zero score weight."

## Never

A hidden, tiny, unselectable or low-contrast link · a `facts.` subdomain · a claim that advertising
raises fetches · borrowing the published hidden-link result for this visible one.
