# 03_fix — contract

**Purpose.** One pull request per fix, in queue order, from one fix skill at a time. A human merges.

**Inputs.**
- Working (this run): `.graded/runs/<date>/02_diagnose.md` (the queue, as the owner left it); `01_read.md` (the before rows); the repository.
- Reference (every run): exactly one of `skills/fix-robots-for-ai-bots/SKILL.md`, `skills/add-llms-txt-and-advertisement-bundle/SKILL.md`, `skills/answer-block-and-faq/SKILL.md`, `skills/json-ld-local-business/SKILL.md`, `skills/nap-consistency/SKILL.md` — the one the current queue item names.
- Do NOT load: the other four fix skills while on one; any other stage.

**Process.**
1. Branch `graded/<fix-skill>` from the default branch.
2. Follow the fix skill. Facts from the site or the owner only.
3. Open the PR: the skill's "Say in the PR" paragraph + the before rows + the recheck line.
4. Append a row to `03_fix.md` (fix, branch, PR URL, rows targeted, merged: pending).
5. Stop; wait for merge or close; update the row; next item.

**Outputs.** One PR per fix; `.graded/runs/<date>/03_fix.md`, last line `Done: yes` when the queue is empty.

**Human check.** The owner merges or closes each PR before the next fix starts.

**Never.** Merge · push to the default branch · stack fixes · invent a fact · hidden text · a claim about rankings, citations or traffic.
