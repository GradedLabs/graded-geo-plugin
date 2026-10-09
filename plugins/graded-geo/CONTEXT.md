# graded-geo — pipeline contract (L1)

**Form.** Pipeline. The same five stages every run; the deliverable is a set of pull requests on
the customer's website repository plus a dated run folder that is the receipt for what changed.

**Factory (this plugin; read-only once installed).** Stage procedures and contracts under
`skills/0N_*/`, the five fix skills under `skills/`, blank run files in `_templates/run/`, and the
two free Graded MCP servers in `.mcp.json`. Nothing here changes per customer.

**Product (the customer's repo).** `.graded/runs/<YYYY-MM-DD>/` — one file per stage, copied from
`_templates/run/README.md` and its siblings, filled by the stage, edited by a person in between.
Fix branches are `graded/<fix-skill>`, one PR each; the run folder rides on those branches.

**Inputs.** The homepage URL, one deep page URL, the repository, and the owner's answers to the
questions a stage asks. Nothing else; no paid data.

**Handoff.** Stage N reads the file stage N−1 wrote. A person may edit any file between stages;
the next stage reads what is there.

**Status.** Derived from files, never from memory: the highest-numbered `0N_*.md` present is the
current stage; a file whose last line is `Done: no` is in progress.

**Human checks.** Confirm the two URLs (stage 1) · read the card and say go (stage 2) · merge or
close each PR (stage 3) · approve the link wording and see it in a browser (stage 4) · decide on
the 30-day re-run (stage 5).

**Never.** A score set by a model or a number out of 100 · a claim about rankings, citations,
mentions or traffic · hidden, tiny or cloaked text · a `facts.` subdomain claim · a paid probe ·
operator skill content · merging · pushing to the default branch.

**Pointers.** Entry `AGENTS.md`. Measurement tools: `check_ai_crawl_access`,
`retrieval_gate_checklist` (free). What the Graded account adds — stored engine answers, the
measured plan — is not in this plugin: `README.md`.
