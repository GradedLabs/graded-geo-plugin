# 02_diagnose — contract

**Purpose.** Turn the recorded rows into the four-answer card as this plugin can see it, with blanks where it cannot, and name the one next fix.

**Inputs.**
- Working (this run): `.graded/runs/<date>/01_read.md`.
- Reference (every run): `SKILL.md` in this folder (the fixed order and the row → fix-skill table).
- Do NOT load: the fix skills; any live tool call (stage 1 already ran them); any other stage.

**Process.**
1. Answer the four questions from the rows; the fourth is always `not measured here` with the account link the tool printed.
2. Next fix = the first FAIL row in the fixed order. Position decides, never judgment.
3. Queue = the remaining FAIL rows in the same order, each mapped to its fix skill.

**Outputs.** `.graded/runs/<date>/02_diagnose.md` filled, last line `Done: yes`.

**Human check.** The owner reads the card and says go, or edits the queue file; stage 3 reads whatever is there.

**Never.** A number out of 100 · a score set by a model · a yes or no on the fourth question · a reordered or padded queue · a claim about rankings, citations or traffic.
