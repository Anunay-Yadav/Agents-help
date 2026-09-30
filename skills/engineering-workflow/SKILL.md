---
name: engineering-workflow
description: Select optional stages and maintain task iterations, status, and handoffs for engineering work using the Agents-help framework. Use when planning, carrying out, or resuming a tracked engineering task; keep quick one-step work lightweight.
---

# Engineering workflow

The human owns the goal, priorities, and major architectural choices. Choose routine implementation details within the request. Complete authorized work without adding approval gates between stages; a requested investigation or design ends at its requested deliverable.

## Select stages

Choose the smallest set that resolves the task's uncertainty and produces its requested outcome. Stages may be skipped, combined, revisited, or reordered. Roles describe responsibilities; stages describe work. One agent can cover several roles.

| Stage | Include when | Typical role |
| --- | --- | --- |
| Problem frame | Goal, scope, or acceptance criteria need clarification | Synthesizer / assigned role |
| Understand system | Existing behavior or constraints need investigation | Explorer |
| Design | Interfaces or tradeoffs need a deliberate decision | Designer |
| Decompose | Work needs independently actionable pieces | Designer / Implementer |
| Implement | The request calls for a change | Implementer |
| Review | A second reasoning pass would catch material defects | Reviewer |
| QA / validate | Evidence is needed that the output meets acceptance criteria | QA / Implementer |
| Integrate | Separate changes must work together or a delivery branch needs preparation | Integrator |
| Synthesize | Findings or decisions need a clear conclusion or handoff | Synthesizer |

Examples, not mandatory pipelines:

- Investigation: problem frame → understand → conclusion.
- Design-only task: problem frame → understand → design; stop there.
- Small bug or plot: understand as needed → implement → focused validation.
- Architecture change: understand → design → review → implement → validate; integrate if needed.
- Performance work: baseline measurement → investigate → change → remeasure.

Skipping a dedicated QA stage does not remove the need for proportionate validation. Use existing checks, a targeted experiment, or visual inspection as appropriate. Clearly distinguish passed, failed, and not-run checks.

## Keep only useful records

For work that benefits from persistence, use the target project's layout:

```text
ai/<task-name>/iteration-01/
├── STATUS.md
├── HANDOFF.md           # only when handing off or pausing
├── 01-understand/       # optional; only selected stages with artifacts
├── 02-implement/
└── 03-validate/
```

Use a short descriptive task slug. Stage numbers reflect the chosen sequence within that iteration, not a universal stage ID. Do not create empty stage folders. Keep short notes in `STATUS.md`; put substantial findings or designs in the relevant stage folder. Product source changes stay in their normal project paths.

Start from [STATUS.md](assets/STATUS.md); adapt or remove unused fields. Record selected stages, consequential skips and why, current evidence, and the next action. Update at meaningful transitions or before pausing, not for every tool call. For a quick task, a chat summary is enough unless persistent records were requested.

Use [HANDOFF.md](assets/HANDOFF.md) when another person, role, or chat needs to resume. Link to evidence rather than copying entire logs. A handoff records work; it does not authorize messaging another chat, merging, publishing, or deploying.

## Iterations

- An iteration is one coherent attempt at the same task goal, not a chat, stage, commit, or agent.
- Resume the current iteration across chats and role changes. Review fixes and ordinary retries stay there.
- Start `iteration-02`, then `iteration-03`, etc. for a deliberate new approach, a materially revised scope, or a new pass after a concluded attempt. Let the human direct a new iteration; if the request already calls for a new pass, proceed and record the reason.
- Give unrelated goals separate task folders. Never overwrite an earlier iteration to make a new one.
- Carry forward only relevant decisions and unresolved items, linking the prior iteration. Historical records remain evidence of that attempt, not current instructions.
- Close an iteration as complete, superseded, or abandoned with its outcome. Mark blocked work honestly, with the dependency and next action; a new chat alone does not unblock it.

On resumption, read the current `STATUS.md`, any `HANDOFF.md`, and the linked artifacts needed for the next action. Verify recorded assumptions against the current working tree before relying on them.
