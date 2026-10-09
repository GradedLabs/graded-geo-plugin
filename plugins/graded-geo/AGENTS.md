# graded-geo — entry (routing only)

You are in the Graded GEO plugin: five numbered stages that make a website's facts readable to a
plain fetch — the way ChatGPT, Claude and Perplexity fetch a page — and prove it with the same free
check before and after. The agent proposes pull requests; a human merges.

| # | Stage | Procedure | Contract | Writes (in the customer's repo) |
|---|---|---|---|---|
| 1 | Read | `skills/01_read/SKILL.md` | `skills/01_read/CONTEXT.md` | `.graded/runs/<date>/01_read.md` |
| 2 | Diagnose | `skills/02_diagnose/SKILL.md` | `skills/02_diagnose/CONTEXT.md` | `02_diagnose.md` — the four-answer card |
| 3 | Fix | `skills/03_fix/SKILL.md` | `skills/03_fix/CONTEXT.md` | one branch + PR per fix; `03_fix.md` |
| 4 | Advertise | `skills/04_advertise/SKILL.md` | `skills/04_advertise/CONTEXT.md` | one PR; `04_advertise.md` |
| 5 | Recheck | `skills/05_recheck/SKILL.md` | `skills/05_recheck/CONTEXT.md` | `05_recheck.md` |

Fix skills — stage 3 loads one at a time, in this order: `skills/fix-robots-for-ai-bots/SKILL.md`,
`skills/add-llms-txt-and-advertisement-bundle/SKILL.md`, `skills/answer-block-and-faq/SKILL.md`,
`skills/json-ld-local-business/SKILL.md`, `skills/nap-consistency/SKILL.md`.

Where things live: the pipeline in one screen `CONTEXT.md` · blank run files `_templates/run/` ·
measurement `.mcp.json` (two free Graded MCP servers, no account) · what this is and is not `README.md`.

Walk: this file → `CONTEXT.md` → the one stage contract → its inputs. Never load every stage.
Status: `ls .graded/runs/<date>/` — the highest-numbered file present is where the run stands; a
file whose last line is `Done: no` is in progress.

Human gates the agent never crosses: merge · publish · send.
Never: a score set by a model · a lift claim · hidden or cloaked text · a paid probe · operator skill content.
