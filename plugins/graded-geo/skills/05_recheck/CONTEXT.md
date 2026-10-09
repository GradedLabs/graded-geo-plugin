# 05_recheck — contract

**Purpose.** Ask the same question again with the same tools on the same URLs, and report rows — not wins.

**Inputs.**
- Working (this run): `.graded/runs/<date>/01_read.md` (before rows and the two URLs); `03_fix.md` (what merged); `04_advertise.md` (the pointer row).
- Reference (every run): `SKILL.md` in this folder; the two MCP servers in `.mcp.json`.
- Do NOT load: the fix skills; any other stage.

**Process.**
1. Confirm with the owner that the merged PRs are live on the real domain.
2. Run `check_ai_crawl_access` and `retrieval_gate_checklist` on the same two URLs.
3. Table: row · before · after · changed. Rows copied verbatim; unchanged rows say `unchanged`; blanks stay blank.
4. The fourth answer stays `not measured here`, with the account link.

**Outputs.** `.graded/runs/<date>/05_recheck.md` filled, last line `Done: yes`, with a suggested re-run date 30 days out.

**Human check.** The owner decides whether to re-run in 30 days and whether to open a Graded account for the fourth answer.

**Never.** Claim a mention, ranking or traffic change · say a fix "worked" beyond its own row · a number out of 100 · re-run against a preview and call it live.
