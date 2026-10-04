# Agents-help

A small global Codex framework: one short `AGENTS.md`, four skills, seven role guides, and two templates. No orchestrator service is required. Engineering presentations require independent final review.

## Install globally

Clone this repository to a stable location. From its root, copy the entry point to your Codex home and the skills to your user skill directory:

```sh
mkdir -p "${CODEX_HOME:-$HOME/.codex}" "$HOME/.agents/skills"
cp -i AGENTS.md "${CODEX_HOME:-$HOME/.codex}/AGENTS.md"
cp -Ri skills/engineering-workflow "$HOME/.agents/skills/"
cp -Ri skills/engineering-roles "$HOME/.agents/skills/"
cp -Ri skills/engineering-slides "$HOME/.agents/skills/"
cp -Ri skills/simple-english "$HOME/.agents/skills/"
```

If you already have global instructions, merge the short entry point into them instead of replacing them. The copy commands prompt before overwriting existing files. Keep all four skill folders intact so their relative links and templates work. Repeat the skill copies when updating.

Codex reads global instructions from its home directory and discovers user skills under `~/.agents/skills`. An existing global `AGENTS.override.md` takes precedence over `AGENTS.md`; incorporate this entry point there if you intentionally use that override. Start a new chat after setup and ask Codex to identify the active global instructions and all four skills.

See the official [AGENTS.md guidance](https://learn.chatgpt.com/docs/agent-configuration/agents-md) and [skill discovery documentation](https://learn.chatgpt.com/docs/build-skills).

## Use

Ask for the outcome and optionally a role:

> Act as Explorer. Trace how authentication works; record findings without implementing changes.

> Fix the CSV export bug. Use only the stages that help and validate the result.

> Design the caching change. Stop after the design and hand it off for review.

An explicit invocation such as `$engineering-workflow` or `$engineering-roles` also selects the corresponding skill. Roles can change within one chat; they do not imply separate agents or permission to contact other chats.

| Resource | Purpose |
| --- | --- |
| [Workflow skill](skills/engineering-workflow/SKILL.md) | Stage selection, task folders, and iteration semantics |
| [Roles skill](skills/engineering-roles/SKILL.md) | Explorer, Designer, Implementer, Reviewer, QA, Integrator, Synthesizer |
| [Engineering slides skill](skills/engineering-slides/SKILL.md) | Worked examples, stable diagrams, progressive builds, and independent review of final exports |
| [Simple English skill](skills/simple-english/SKILL.md) | Plain-English replies and documentation |
| [STATUS template](skills/engineering-workflow/assets/STATUS.md) | Current goal, selected stages, evidence, next action |
| [HANDOFF template](skills/engineering-workflow/assets/HANDOFF.md) | Enough context for the next person or agent |

Task records belong in the project being worked on, under `ai/<task-name>/iteration-XX/`. They do not belong in the global installation. Quick one-step tasks can stay in chat; use persistent records when resuming or handing work off would benefit from them.

Simple English defaults to Plain mode. Requested formats, including the coding-task summary, take precedence over its formatting rules. You can also invoke it with `$simple-english`.

Use `$engineering-slides` to create or revise presentations that explain systems, code, algorithms, or implementation mechanisms. Research presentations need an adapted workflow. The skill requires independent review of the exported slides against source evidence and reconstructed calculations. If evidence or independent review is unavailable, report verification as incomplete. Self-review alone does not satisfy the final review.

The Simple English skill and its references are unchanged copies from [AminBlg/SimpleEnglish](https://github.com/AminBlg/SimpleEnglish/tree/79b590fc8596523d92c26b1ea7e33236606ef069/skills/simple-english), version 2.1.0. The source commit is `79b590fc8596523d92c26b1ea7e33236606ef069`. Its [MIT license](skills/simple-english/LICENSE) is included.
