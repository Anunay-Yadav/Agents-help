---
name: engineering-workflow
description: Select optional stages and maintain task progress and indexes of reusable findings for engineering work using the Agents-help framework. Use when exploring a codebase or planning, carrying out, or resuming a tracked task; keep quick one-step work lightweight.
---

# Engineering workflow

The human owns the goal, priorities, and major architectural choices. Choose routine implementation details within the request. Complete authorized work without adding approval gates between stages; a requested investigation or design ends at its requested deliverable.

## Reuse prior findings

Before exploring project code, read `ai/index.md` if it exists. Look for relevant areas, code paths, and findings, even from differently named tasks. Follow the relevant `ai/<task-name>/index.md`, then only the evidence or iteration records needed for the current question.

Avoid reading unrelated tasks or entire iteration histories. If an index is missing or has no relevant finding, use a focused code search. An index is a navigation aid. Confirm relevant findings against current code before relying on them.

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
ai/
├── index.md                    # small map of reusable findings
└── <task-name>/
    ├── index.md                # findings, evidence, and iteration links
    └── iteration-01/
        ├── STATUS.md
        ├── HANDOFF.md          # only when handing off or pausing
        ├── 01-understand/      # optional; selected stages with artifacts
        ├── 02-implement/
        └── 03-validate/
```

Use a short descriptive task slug. Stage numbers reflect the chosen sequence within that iteration, not a universal stage ID. Do not create empty stage folders. Keep short notes in `STATUS.md`; put substantial findings or designs in the relevant stage folder. Product source changes stay in their normal project paths.

Start from [STATUS.md](assets/STATUS.md); adapt or remove unused fields. Record selected stages, consequential skips and why, current evidence, and the next action. Update at meaningful transitions or before pausing, not for every tool call. For a quick task, a chat summary is enough unless persistent records were requested.

Use [HANDOFF.md](assets/HANDOFF.md) when another person, role, or chat needs to resume. Link to evidence rather than copying entire logs. A handoff records work; it does not authorize messaging another chat, merging, publishing, or deploying.

## Maintain small indexes

When tracking a task, create `ai/index.md` and `ai/<task-name>/index.md` if absent. Use the [AI index template](assets/AI-INDEX.md) and [task index template](assets/TASK-INDEX.md). Keep progress in `STATUS.md`. Reuse the same task index across iterations and chats.

- Keep `ai/index.md` a small map of explored areas and reusable findings. Prefer one short row per area. Combine overlapping discoveries and link to relevant task indexes. Omit routine activity, task states, and a complete task catalog.
- Keep the task index a concise account of what the task established or left unresolved. Link each finding to its evidence, relevant code paths, and source revision when needed. Link the current `STATUS.md` and summarize each iteration in one line.
- Update the task index when findings change, an iteration starts or closes, or work pauses. Update the root index only when reusable findings or their links change. Keep detailed explanations and logs in linked artifacts.
- Add only findings useful to future work. Mark unresolved questions and stale or superseded findings explicitly. Replace outdated summaries when evidence changes, and preserve historical evidence in its iteration.
- For existing tasks, add missing indexes as those tasks are used. Do not read every old task to build a complete catalog.

## Iterations

- An iteration is one coherent attempt at the same task goal, not a chat, stage, commit, or agent.
- Resume the current iteration across chats and role changes. Review fixes and ordinary retries stay there.
- Start `iteration-02`, then `iteration-03`, etc. for a deliberate new approach, a materially revised scope, or a new pass after a concluded attempt. Let the human direct a new iteration; if the request already calls for a new pass, proceed and record the reason.
- Give unrelated goals separate task folders. Never overwrite an earlier iteration to make a new one.
- Carry forward only relevant decisions and unresolved items, linking the prior iteration. Historical records remain evidence of that attempt, not current instructions.
- Close an iteration as complete, superseded, or abandoned with its outcome. Mark blocked work honestly, with the dependency and next action; a new chat alone does not unblock it.

On resumption, follow the relevant task index to the current `STATUS.md`, any `HANDOFF.md`, and only the artifacts needed for the next action. If the task index is missing, use the known iteration records directly. Verify recorded assumptions against the current working tree before relying on them.
