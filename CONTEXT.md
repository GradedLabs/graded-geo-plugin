# graded-geo-plugin — repository contract (L1)

**Form.** A marketplace with one plugin bundle. `.claude-plugin/marketplace.json` names it;
`plugins/graded-geo/` is the bundle, itself an ICM pipeline (`plugins/graded-geo/CONTEXT.md`).

**Universes.** Everything here is live; there is no leftover or ghost. The tree is regenerated
whole on every publish from the private repository's publish script. Nothing is edited in place.

**Inputs.** A Claude Code session with this marketplace added (`README.md`), a website repository,
its homepage URL and one deep page URL. No account, no paid data: the two Graded MCP servers in
`plugins/graded-geo/.mcp.json` are free.

**Outputs.** In the customer's repository only: `.graded/runs/<date>/` (one file per stage, the
receipt) and one pull request per fix. This repository never changes at run time.

**Name collisions.** *run* = a dated run folder in the customer repo, not a CI run · *skill* = a
stage or fix procedure under `plugins/graded-geo/skills/`, not an Agent Skills API object ·
*advertise* = stage 4, naming a fact file where models read, not advertising copy.

**Human gates.** Merge · publish · send. The agent proposes; a person merges every PR. A model never
sets a score; no claim about rankings, citations, mentions or traffic; no hidden text; no paid probe.

**Token note.** Cold walk = `AGENTS.md` + `plugins/graded-geo/AGENTS.md` + one stage contract,
about 1.3k tokens before any task input.

**Pointers.** Product and account: https://usegraded.com · issues: this repository.
