---
name: engineering-slides
description: >
  Create or revise engineering presentations that explain systems, code,
  algorithms, and implementation mechanisms through consistent diagrams,
  worked examples, clear transitions, and concise summaries. Use when the
  audience needs to follow how a system works or how its state changes.
  Research presentations require a separate adapted workflow.
---

# Engineering Slides

Create slides that help the audience follow the mechanism, understand each
change, and retain the overall flow.

Prefer fewer slides when content can be combined clearly. Keep additional
slides when they make a difficult operation easier to follow. Do not force
either a short deck or a long deck.

Honor the user's template, requested scope, protected content, and pacing.

## 1. Build the explanation around the engineering flow

- Establish the relevant setup, components, and inputs before explaining
  operations.
- Follow the actual dependency or execution order.
- For each operation, explain the starting state, what the operation does,
  and the resulting state.
- Introduce symbols and indices before using them in equations.
- Keep the audience's attention on the current operation and what changed.
- Put supporting implementation details and source references in speaker
  notes when they do not belong in the main explanation.

Do not force setup, layout, and inputs onto separate slides when one clear
slide can introduce them.

## 2. Use one consistent worked example

Choose a small example that exposes the important behavior. Include enough
variation to demonstrate operations that would otherwise appear unnecessary.

- Keep names, identifiers, colors, values, and ownership consistent.
- Carry the same example through the complete explanation.
- Show actual intermediate values where they clarify the mechanism.
- Derive tables, equations, diagrams, and outputs from one shared example.
- Check independent expected results and relevant conservation rules.
- State which parts are illustrative and which come from an actual system.

If the example changes, update every dependent slide and check the results.

## 3. Keep the visual context stable

Unless a template specifies another layout, use:

- A stable diagram or worked state on the left.
- A concise explanation and relevant equations on the right.
- A small progress strip at the bottom for a multi-stage process.

Keep component positions, labels, and semantic colors fixed across related
slides. Move objects only when movement represents an actual change.

Use labels as well as color to identify objects and changes. Reserve enough
space for the complete explanation before creating progressive builds.

## 4. Make transitions explain the change

Carry the previous state into the next slide. Highlight the affected objects,
new information, or changed values. Keep unchanged context visible but quiet.

- Show what remains fixed.
- Show the current operation.
- Show what changed because of that operation.
- Explain why the resulting state enables the next step.

Use slow, simple transitions when the presentation format supports them.
Prefer presenter-controlled advances so the audience can inspect the new
state. Avoid motion that does not explain the mechanism.

For static slides or PDF, use successive states with the same geometry.
The audience must be able to compare them without searching for moved objects.

## 5. Use progressive builds without creating redundancy

Design the complete stage first. Split it into builds only when showing
everything together makes the explanation difficult to follow.

A build is one meaningful addition or state change. It is not automatically
one sentence, one equation line, or one label.

- Keep a heading with the information that gives it meaning.
- Group tightly related explanations, equations, and values.
- Retain earlier content when later content depends on it.
- Keep previously visible text and formula lines at fixed positions.
- Do not reflow or recenter content as new material appears.
- Do not reveal incomplete mathematical expressions.

For multi-line formulas, preserve the final line positions and baselines.
Check rendered positions because unchanged text boxes do not guarantee
unchanged glyph positions.

Do not create a new slide when it adds no useful explanation, state change,
or opportunity to inspect a difficult step.

## 6. Remove obvious repetition before delivery

Review neighboring slides together.

Merge slides when their content forms one readable explanation and separating
them adds little teaching value. Remove repeated definitions, identical
takeaways, and narration that merely describes an already clear diagram.

For cumulative builds, retaining the final build can replace earlier pages
when the combined explanation remains easy to follow. Preserve all necessary
information when doing this.

Do not compress several dependent operations into an unreadable slide merely
to reduce the slide count. Let comprehension determine the final length.

## 7. Add summaries at natural checkpoints

After a few related operations, add a short summary before introducing another
substantial part of the system.

A useful summary shows:

- What the preceding operations accomplished.
- The current state of the worked example.
- The dependency or question that leads into the next section.

Use a compact diagram, a short sequence, or a few concrete statements.
Consolidate the explanation instead of replaying every previous slide.

End with a recap of the complete flow and its engineering implications.
Choose summary locations from the structure of the explanation, not a fixed
slide interval.

## 8. Keep technical claims faithful to the evidence

For code-grounded explanations, inspect the relevant entrypoint, caller,
configuration, and implementation. Record the source revision when it matters.

- State assumptions that change the behavior.
- Distinguish the teaching model from the actual implementation.
- Distinguish source-supported behavior from measured runtime behavior.
- Show what each component knows at each stage.
- Distinguish unknown information from a known zero value.
- Preserve units, data ordering, ownership, and mathematical meaning.
- Qualify algebraic equivalence when finite precision changes the result.

Do not infer actual overlap from an asynchronous API or physical traffic from
logical payload sizes. Explain these distinctions only where they affect the
audience's understanding.

Put precise source references and necessary qualifications in speaker notes.

## 9. Generate editable and consistent artifacts

Honor the requested output formats. Otherwise, prefer editable PPTX and a
matching PDF.

Keep text, diagrams, tables, and formulas editable where practical.

For programmatic generation, define content and geometry once and reuse them
across exports. Preserve the generator, example data, and slide sequence when
they are needed to reproduce the result.

A shared scene definition improves consistency. It does not prove that
PowerPoint and another renderer display the deck identically.

## 10. Check the actual exported presentation

Validate the files that will be delivered, not only the outline or generator.

- Check slide order, titles, notes, and requested content.
- Check example arithmetic, intermediate states, and final results.
- Check clipping, overlap, alignment, text fit, and formula readability.
- Check fixed geometry across progressive builds.
- Check that PPTX and PDF contain the intended corresponding content.
- Inspect every contact sheet for overall pacing and consistency.
- Inspect dense, changed, and important slides at full size.

Review technical accuracy and visual clarity separately. Complete the required
independent adversarial review in section 12. Self-review does not replace it.

After the last correction, check the final export again. State any material
validation limit, including whether native PowerPoint rendering was tested.

## 11. Make revisions precise

Treat the latest accepted deck as the starting point.

Apply requested merges, deletions, corrections, and regrouping exactly.
Preserve protected slides, established geometry, and unrelated content unless
the user requests a change.

After structural edits, update slide numbers, progress indicators, summaries,
and transition cues.

Keep prior accepted outputs available. Describe preservation precisely:
identify which content, data, or geometry remained unchanged.

Deliver the requested files with a brief account of the changes, checks,
and any remaining limitation.

## 12. Required final adversarial verification

The final presentation must pass independent adversarial review.
The author's self-review alone does not satisfy this stage.

Reviewers must challenge the presentation against authoritative evidence,
not merely assess whether its explanation sounds plausible.

### Extract and cover the complete presentation

Review the actual exported files, not only the generator or outline.

Extract and inspect:

- All slide text, captions, definitions, and speaker notes.
- Equations, numerical examples, intermediate values, and table cells.
- Chart values, axes, units, legends, and stated conclusions.
- Diagram labels, arrows, ownership, ordering, and state changes.
- Progressive builds, transition explanations, and summary slides.

Inspect rendered slides as well as extracted text. Text extraction alone
does not capture relationships conveyed by position, arrows, or highlighting.

Maintain a coverage record so no slide or factual claim escapes review.

### Check against hard evidence

For each engineering claim, identify the supporting evidence.

Use relevant source code and configuration, official specifications,
original data, recorded logs, or independently checked calculations.
Record versions and source locations where behavior depends on them.

Do not treat another slide, the author's explanation, or generated prose
as independent evidence.

Reconstruct worked examples independently. Check intermediate states,
dimensions, units, ordering, ownership, and final results.

Distinguish verified facts, illustrative assumptions, and explicit inferences.
An illustrative example must remain internally correct and consistent with
its stated assumptions. An inference must not be presented as an observed fact.

### Use independent adversarial reviewers

Assign complementary review scopes:

- Source fidelity and implementation behavior.
- Numerical examples, equations, and data consistency.
- Whole-deck contradictions, missing assumptions, and misleading implications.

Combine or divide scopes according to complexity. Ensure the combined review
covers the complete deck, including notes and summaries.

Give reviewers the final artifacts and underlying evidence. Require them
to report each finding with its slide, claim, evidence, impact, and correction.

Reviewers must verify the evidence themselves rather than adopt the author's
conclusions.

### Resolve findings and recheck the final export

Correct factual errors, unsupported statements, and misleading diagrams.
Remove or explicitly qualify claims that the available evidence cannot support.

Regenerate the affected exports and repeat the relevant reviews.
Check dependent slides and summaries after each substantive correction.

Any later edit invalidates verification of the affected content.

### Pass criteria

This stage passes only when:

- Every slide and factual claim has a recorded review disposition.
- Technical claims agree with the applicable authoritative evidence.
- Worked examples and calculations pass independent reconstruction.
- Diagrams, notes, transitions, and summaries agree with one another.
- No unresolved factual error or unsupported factual assertion remains.
- Reviewers confirm that their findings are resolved in the final exports.

Record the verdict, coverage, evidence references, resolved findings,
remaining explicit limitations, and identity of the reviewed files.

If required evidence or independent review is unavailable, mark verification
incomplete. Do not label the presentation verified or ready for final delivery.
