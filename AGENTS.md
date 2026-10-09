# graded-geo-plugin — entry (routing only)

This repository is the public marketplace for one Claude Code plugin, `graded-geo`: five numbered
stages that make a website's facts readable to a plain fetch and prove it with the same free check
before and after. Fixes arrive as pull requests; a human merges.

| Need | Go to |
|---|---|
| Install | `README.md` |
| The plugin's entry (routing only) | `plugins/graded-geo/AGENTS.md` |
| Pipeline contract, human gates | `plugins/graded-geo/CONTEXT.md` |
| One stage's procedure and contract | `plugins/graded-geo/skills/` (`01_read` … `05_recheck`) |
| Blank run files the stages copy into a customer repo | `plugins/graded-geo/_templates/run/` |
| What this repository is and is not | `CONTEXT.md` |

Walk: this file → the plugin entry → one stage contract → its inputs. Never load every stage.
This tree is generated from the private GradedLabs repository on every publish; edits here are
overwritten — open an issue instead.
