# 04_advertise — contract

**Purpose.** Make the fact file findable from the page a model is already reading — visibly — and verify the pointer row afterwards.

**Inputs.**
- Working (this run): `.graded/runs/<date>/03_fix.md` (did an llms.txt land?); `01_read.md` (the before pointer row); the repository.
- Reference (every run): `SKILL.md` in this folder; `skills/add-llms-txt-and-advertisement-bundle/SKILL.md` section "Advertise it".
- Do NOT load: the other fix skills; any other stage.

**Process.**
1. Branch `graded/advertise-llms-txt`.
2. Visible footer link (owner approves the wording) · head `<link rel="alternate">` · robots.txt line where allowed · sitemap entry where allowed.
3. Tripwire: grep the diff for hiding markup; open the page in a browser; a person must see and click the link.
4. Open the PR with the "Say in the PR" paragraph and the before row.
5. After merge and deploy: run `check_ai_crawl_access`; record the after row.

**Outputs.** One PR; `.graded/runs/<date>/04_advertise.md` with the pointer row before and after, last line `Done: yes`.

**Human check.** The owner approves the link wording and confirms the link is visible and clickable in a browser.

**Never.** Hidden, tiny, unselectable or low-contrast links · a `facts.` subdomain · a claim that advertising raises fetches · ticking the sitemap row the tools cannot see.
