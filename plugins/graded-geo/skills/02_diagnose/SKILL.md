---
name: 02_diagnose
description: Stage 2 of the Graded GEO walk. Turns the rows from 01_read into the four-answer card as the plugin can see it — can AI read it, is it answer-ready, does the page point to its fact file, is the business named by the four engines (always "not measured here") — and names the one next fix by position in a fixed order. Use after 01_read, or when asked "what should I fix first for AI search".
---

# 02_diagnose — the four-answer card

Contract: `CONTEXT.md` beside this file. Input: `.graded/runs/<date>/01_read.md`. Load nothing else.

## The card (fill the template; blanks stay blank)

1. **Can AI read it?** — from `check_ai_crawl_access`: loads without JavaScript, words readable,
   the robots rows, any bot wall. Answer yes / no / unmeasured, and name the row that says so.
2. **Is it answer-ready?** — from `retrieval_gate_checklist`: the answer-block row and the text floor.
3. **Does the page point to its fact file?** — the "Page points to llms.txt" row: yes / no / hidden / unmeasured.
4. **Is the business named by ChatGPT, Gemini, Google AI Overviews and Perplexity for its keyword?** —
   **not measured here.** This plugin never asks an engine. Copy the sentence from the template and
   the Graded account link the tool printed. Never guess yes or no.

## The next fix — by position, never by judgment

The next fix is the **first FAIL row in this fixed order** — the same order the checklist prints,
with NAP last: robots → text without JavaScript → answer block → llms.txt → page points to llms.txt →
JSON-LD → NAP (from the `01_read` counts: more than one distinct form = FAIL). Map it to a fix skill:

| FAIL row | Fix skill |
|---|---|
| robots | `fix-robots-for-ai-bots` |
| text without JavaScript | out of scope — tell the owner the page is client-rendered and stop until it is server-rendered; nothing below will be read either |
| answer block | `answer-block-and-faq` |
| llms.txt, or page points to llms.txt | `add-llms-txt-and-advertisement-bundle` (the pointer is finished and verified in `04_advertise`) |
| JSON-LD | `json-ld-local-business` |
| NAP | `nap-consistency` |

List the remaining FAIL rows in the same order as the queue. Do not reorder for impact, do not add
items the rows did not raise, do not drop a FAIL because it looks small.

## Finish

Set `Done: yes`. Show the owner the card and the queue and wait for "go" — they may edit the queue
file, and stage 3 reads what is there. No number out of 100 appears anywhere on the card.
