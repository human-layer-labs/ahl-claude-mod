# v0.2 decision-flow enforcement

Runtime enforcement for AHL's “Act is the default” and “No New Evidence, No New Round” decision flow was investigated and **deferred**.

The observed evidence does not justify interception:

- Historical review rounds did not expose a sufficiently reliable discrete runtime signal. In this environment they were launched as shell commands and untyped, general-purpose subagents; none used a review-specific agent type or review skill. A type-based gate would therefore have intercepted none of them. Distinguishing rounds would require reading free text, which is rejected.
- Human-question gating would currently tax more legitimate questions than clearly unnecessary ones. In a rough, single-rater sample of 60 structured questions from one environment and period, about 62% were clearly Human-owned and about 13% clearly Agent-owned.
- Most importantly, the newly revised AHL Skill had not yet been deployed in the observed environment. The claim that the current semantic policy is insufficient is not established.

## Current stance

**AHL Micro is now the current runtime baseline (2026-10-09).** No Mod, gate, hidden salience injection, or change to how review rounds are launched.

Do not compensate for old AHL startup/review Tax by moving that same ceremony into a Claude-specific layer. In particular, do not preload long AHL references, inject them every turn, or add a generic STOP/review wrapper around AHL Micro.

Measure the deployed AHL Micro by itself. Reopen the Mod question only if repeated, material failures remain and a distinct Claude runtime signal can address them with less cost than the failure it prevents.

## Considered controls

- **Salience-only:** hidden per-prompt context or a sentence in tool descriptions. Admissible next only if evidence shows the policy alone is not enough.
- **Discrete transition gate:** a deny-once “bump” on a repeated, typed review. This is the right shape, but reviews need to pass through a discrete channel. The workflow will not be changed merely to make a gate easier.
- **Semantic runtime classifier:** rejected.

## Repeating the evidence check

Read local Claude Code session records, read-only, and report aggregate counts only; send nothing anywhere. Per period, count subagent starts and their agent types, skill invocations by name, structured Human questions, and shell commands that launch an external model round. Optionally classify a small sample of Human questions by who owned the choice. The record format is not a stable contract, so no script is shipped.

## Reopen condition

Reopen if over-review or unnecessary Human questions recur under the deployed current Skill and re-measurement shows which failure remains. Apply the next control only to that remaining failure.
