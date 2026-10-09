# 01_read — contract

**Purpose.** See the site the way a plain fetch sees it. Facts only; no judgment yet.

**Inputs.**
- Working (this run): the homepage URL and one deep page URL (the owner gives them); the repository checkout.
- Reference (every run): `SKILL.md` in this folder; the two MCP servers in `.mcp.json`.
- Do NOT load: any other stage; the fix skills; the owner's analytics.

**Process.**
1. Create `.graded/runs/<date>/` from `_templates/run/` if absent.
2. Run `check_ai_crawl_access` and `retrieval_gate_checklist` on both URLs.
3. Locate the robots, sitemap, llms.txt, head, footer and JSON-LD sources in the repo; count where name, address and phone appear.
4. Record every tool row verbatim; where a tool could not check, write `unmeasured`.

**Outputs.** `.graded/runs/<date>/01_read.md` filled, last line `Done: yes`.

**Human check.** The owner confirms the two URLs are the right pages before stage 2 starts.

**Never.** Guess what a crawler sees · call a paid probe · write `0` or `FAIL` for anything not checked · propose a fix.
