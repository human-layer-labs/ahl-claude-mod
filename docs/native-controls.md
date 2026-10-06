# AHL and Claude Code responsibility map

v0.1 documents ownership; it installs no hooks, interceptors, state, rules or runtime enforcement. AHL supplies semantic authority and policy. Claude Code supplies native controls according to the active configuration. A future AHL Claude Mod may add only mechanical enforcement that passes the gate below.

| Concern | Primary owner | Why the Mod does not duplicate it in v0.1 |
| --- | --- | --- |
| Goal, Target and Authorization | AHL | These are semantic decisions grounded in attributable Human authority; a runtime path check cannot establish them. |
| Scope semantics | AHL | Meaning and scope are contextual; workspace access does not establish permission. |
| Human-owned decisions | AHL / Human | The Agent represents attributable Human authority; it does not create authority. Material Human choices remain with the Human. |
| Native tool permission checks | Claude Code | Use its permission controls where enabled and applicable. A Mod permission wrapper would duplicate that layer. |
| Sandbox and host isolation | Claude Code / host configuration | Their availability and coverage depend on configuration and execution mode; the Mod makes no universal protection claim. |
| Project-specific deny rules | Claude Code / project policy | Projects can declare exact protected effects in their Claude Code policy, such as one exact MCP tool name or an `Edit(...)` path. This repository ships no default deny list. |
| Destructive shell protection | Existing Claude Code controls where applicable | Native permission behavior, auto mode, sandboxing and managed settings vary by setup. A Mod command-pattern rule would duplicate controls and rely on a brittle signal. |
| Recovery semantics | AHL | AHL determines recovery meaning and requirements; the Mod adds no recovery machinery. |
| Review-round admission | AHL semantic policy | Whether another review is needed is a semantic policy decision, not a Mod gate. |
| Completion semantics | AHL | AHL owns what completion means; the Mod has no reliable independent completion signal. |
| Host Roots / workspace access | Claude Code | Reachability is mechanical capability. Being inside Host Roots does not establish AHL Authorization. |

## Runtime implementation gate

Runtime Mod code is reconsidered only when a Need trigger **and** every Feasibility condition hold.

**Need — at least one must be evidenced:**

- A real uncovered Claude Code action crosses a material boundary despite existing controls.
- Repeated false behavior is observed that semantic AHL cannot reliably prevent.
- The user intentionally operates in a permission-bypass configuration that requires an additional mechanical containment layer.

**Feasibility — all must hold:**

- A reliable runtime signal exists.
- The control can make a narrow, truthful claim.
- False-positive STOP risk is low.
- Ordinary-work overhead is negligible.
- The control causes no unnecessary Human escalation.
- There is a clear condition for removing it.

If both triggers do not hold, do not implement the Guard.

## Deferred designs

- Runtime Authorization Envelope: no unique protection that justifies a second authority mechanism.
- Root/path fence: workspace reachability is not authority, and the signal can be incomplete.
- Destructive-command regex Floor: command-pattern matching is unreliable and duplicates native controls where they apply.
- Review gate: duplicates AHL semantic policy and can add review Tax without a reliable signal.
- Recovery gate: duplicates AHL Recovery semantics without a distinct runtime need.
- Completion gate: lacks a reliable independent completion signal and duplicates AHL semantics.
- Broad DENY-on-UNKNOWN behavior: uncertainty alone can create false-positive STOPs and unnecessary Human Tax.

These designs remain deferred unless the runtime implementation gate is met. Ordinary bounded, recoverable implementation should continue without new ceremony. Established protected boundaries should stop at the layer that can enforce them most reliably. The Mod must not create work merely to justify its own existence.
