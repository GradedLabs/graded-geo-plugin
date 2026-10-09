---
name: 03_fix
description: Stage 3 of the Graded GEO walk. Works the fix queue from 02_diagnose one fix skill at a time — robots.txt for AI bots, the llms.txt bundle, answer block and FAQ, LocalBusiness JSON-LD, NAP consistency — each as its own branch and pull request with the before rows attached. A human merges. Use after 02_diagnose, or when asked to "apply the Graded fixes" or "open the GEO fix PRs".
---

# 03_fix — one fix, one branch, one PR

Contract: `CONTEXT.md` beside this file. Input: the queue in `.graded/runs/<date>/02_diagnose.md`
(the owner may have edited it; read the file, not your memory).

## Loop — once per queue item

1. `git switch -c graded/<fix-skill>` from the default branch. You are already in a worktree.
2. Load **only** that fix skill's `SKILL.md` and follow it top to bottom. Every fact comes from the
   site or from the owner in writing; a missing fact is a question, never a guess.
3. Commit the change and the updated run folder. Open the pull request. Body = the skill's
   "Say in the PR" paragraph, the before rows copied from `01_read.md` for the rows this fix targets,
   and the line "After merge, stage 05_recheck re-runs the same check." Nothing about rankings,
   citations, mentions or traffic.
4. Append a row to `03_fix.md`: fix skill, branch, PR URL, rows targeted, `merged: pending`.
5. **Stop.** Report the PR to the owner. Do not start the next fix until they say merged or closed;
   then update the row and continue with the next queue item.

## When the queue is empty

Set `Done: yes`. If an llms.txt now exists (new in this run or already there), the next stage is
`04_advertise`; otherwise it is `05_recheck`.

## Never

Merge · push to the default branch · stack two fixes in one PR · add hidden text · state a fact the
page does not back · skip a queue item because it looks small.
