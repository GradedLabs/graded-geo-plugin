---
name: 05_recheck
description: Stage 5 of the Graded GEO walk. Asks the same question again — the same two free tools on the same two URLs — after the fixes are merged and live, and reports before/after rows without claiming any mention, ranking or traffic change. Use after 03_fix or 04_advertise, or when asked "did the fixes work" or "re-run the Graded check".
---

# 05_recheck — the same question, later

Contract: `CONTEXT.md` beside this file. Inputs: `01_read.md` (before), `03_fix.md`,
`04_advertise.md` in `.graded/runs/<date>/`.

## Steps

1. Wait until the owner says the merged PRs are live on the real domain. Do not re-run against a preview.
2. Run `check_ai_crawl_access` and `retrieval_gate_checklist` on the **same two URLs** recorded in `01_read.md`.
3. Fill the table in `05_recheck.md`: row · before · after · changed. Copy rows exactly as printed.
4. Rows that did not change say `unchanged`. Rows that were `unmeasured` before and still are stay blank.
5. The fourth answer — is the business named by ChatGPT, Gemini, Google AI Overviews or Perplexity —
   stays **not measured here**. Point to the Graded account line the tool printed; that check asks the
   four engines and stores every answer, dated.
6. Set `Done: yes`. Suggest a re-run in 30 days; the owner decides.

## What this stage may say

"This row changed from X to Y." · "This row did not change." · "Not measured here."

## What it never says

"The fix worked" beyond its own row · anything about rankings, citations, mentions or traffic ·
a number out of 100 · a prediction about what any engine will do next.
