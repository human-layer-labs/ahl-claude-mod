# AHL Claude Mod

A Claude Code-specific integration point for Agent Human Layer (AHL). This repository is separate from [`agent-human-layer`](https://github.com/human-layer-labs/agent-human-layer) so the provider-independent AHL policy does not depend on a Claude Code integration.

## v0.1: documentation only

The v0.2 decision-flow enforcement decision is recorded in [docs/decision-flow.md](docs/decision-flow.md).

v0.1 deliberately contains no runtime enforcement. Claude Code's native controls remain responsible for its configured permission checks, sandbox and host security; AHL owns semantic Goal, Target, Authority and Boundary reasoning. The middle integration layer is empty until evidence shows it is needed. The absence of code is an architecture decision, not unfinished work.

Claude Code behavior depends on configuration and execution mode. Permission modes, auto mode, `bypassPermissions` and `--dangerously-skip-permissions`, managed settings, and sandbox availability affect which native controls apply. This project makes no claim that native controls protect every configuration or execution mode. In particular, workspace reachability (“Host Roots”) is capability, not AHL Authorization.

AHL is moving toward “Lightweight. Fast. Recoverable.” and “Act is the default” because accumulated reviews, re-reviews, recovery checks, policy rereads and confirmation rounds slowed ordinary implementation. Do not add a Guard unless Evidence shows an uncovered material failure it can prevent. A false-positive STOP is a first-class failure.

Runtime Mod code may be reconsidered only when both the Need and Feasibility triggers in the [native controls map](docs/native-controls.md#runtime-implementation-gate) hold. Any future Guard must make a narrow, reliable claim, add negligible ordinary-work overhead, avoid unnecessary Human escalation, and have a clear removal condition.

Ordinary bounded, recoverable implementation should continue without new ceremony. Established protected boundaries should stop at the layer that can enforce them most reliably.

The Mod must not create work merely to justify its own existence.
