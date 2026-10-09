# graded-geo — Claude Code plugin

The Graded GEO walk for a website repository: five numbered stages that make a site's facts
readable to a plain fetch (the way ChatGPT, Claude and Perplexity fetch a page) and prove it with
the same free check before and after. Fixes arrive as pull requests. A human merges. Built by
[Graded](https://usegraded.com).

## The walk

| # | Stage | What it does | Writes |
|---|---|---|---|
| 1 | `01_read` | Runs the two free Graded checks on the homepage and one deep page; finds the robots, sitemap, llms.txt, head, footer and JSON-LD sources in the repo | `.graded/runs/<date>/01_read.md` |
| 2 | `02_diagnose` | The four-answer card — can AI read it, is it answer-ready, does the page point to its fact file, is the business named by the four engines (always "not measured here") — and the one next fix, by position in a fixed order | `02_diagnose.md` |
| 3 | `03_fix` | One fix skill at a time, one branch and one PR each, with the before rows attached | PRs; `03_fix.md` |
| 4 | `04_advertise` | The reverse-mullet step: a visible footer link, a head link, a robots.txt line and a sitemap entry so the fact file is named where a model reads — no hidden text | one PR; `04_advertise.md` |
| 5 | `05_recheck` | The same two checks on the same two URLs, after the merges are live; before/after rows, no claims | `05_recheck.md` |

Status is read from files: the highest-numbered file in `.graded/runs/<date>/` is where the run
stands. Blank run files live in `_templates/run/`; stage 1 copies them. Entry file for the agent:
`AGENTS.md` (routing only, under 800 tokens); the pipeline contract: `CONTEXT.md`; one `CONTEXT.md`
contract per stage. The `geo-remediator` agent walks these in an isolated worktree.

## The fix skills (stage 3 loads one at a time)

| Skill | Fix it makes |
|---|---|
| `fix-robots-for-ai-bots` | Allow the named AI crawlers in `robots.txt`, or block them on purpose, with a diff you can read |
| `add-llms-txt-and-advertisement-bundle` | Add `/llms.txt` built from the sitemap, plus a visible footer link and `<link rel="alternate">` so it is advertised without hidden text |
| `answer-block-and-faq` | Put a short, direct answer about the business near the top of a page and a real FAQ below it |
| `json-ld-local-business` | Add `LocalBusiness` JSON-LD with only facts the site already states |
| `nap-consistency` | Find and align name, address and phone across pages |

## Why stage 4 exists

A fact file nothing links to is rarely fetched. In the one published test, a model fetched a
site's llms.txt only once the page it was reading named the file — and that test used a hidden
9px link. We will not install hidden text on a business's site. The plugin ships the visible
version, checks it with the "Page points to llms.txt" row the free tools now print, and does not
claim its effect. Google says it does not use these files; the file carries zero score weight.

## Measurement

The two free Graded MCP servers in `.mcp.json` — `check_ai_crawl_access` and
`retrieval_gate_checklist` — back every row. Each answer says what a plain fetch can read, names
the one next fix, and ends with the free report link and one sentence about the Graded account.
Nothing here claims a ranking or a mention.

## Install

```bash
claude plugin marketplace add GradedLabs/graded-geo-plugin
claude plugin install graded-geo@graded-geo-plugin
```

Or load it straight from a checkout while developing: `claude --plugin-dir ./plugins/graded-geo`.
Start a run with `/graded-geo:01_read`, or ask the `geo-remediator` agent to run the walk.

## What it never contains

The Graded measurement skill (`tub-students-geo-domination-v1`), the derivers, and any stored
engine answers. Those are served to paying customers through the account-gated Graded
connector, which is planned (`docs/MCP-CONNECTOR-PLAN.md` in the Graded repo) and not yet live.
`.mcp.json` lists only the two free endpoints today; when the connector ships, this entry is
added so the agent can read the customer's measured fix list:

```json
"graded-account": { "type": "http", "url": "https://usegraded.com/api/mcp/connector" }
```

This plugin is the fix list; the connector is the measurement.

## Honesty rules (apply to every PR the agent writes)

- Never write that llms.txt, schema or any fix improves rankings, citations or visibility.
- Never write that Google reads the file; Google has said it does not.
- Never claim that advertising the file raises fetches; the visible variant is unmeasured.
- Only state facts the site already states; never invent hours, addresses or claims.
- Unmeasured is not zero. Say "not checked" when it was not checked.
- No score out of 100 anywhere; the plugin prints rows, not numbers.
