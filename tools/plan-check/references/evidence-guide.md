# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

Eval: compare the issue description and the `## Repro evidence` block's trigger, observed output and controls with the candidate plan's cause sentence. Live: use the issue thread and this student's posted week-2 repro, then the draft plan. Good: the cause or labeled hypothesis explains the distinctive before/control difference; a cause ruled out by a control fails even if a maintainer speculated about it.

## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

Eval: read the candidate plan's change, in/out boundaries and files against the issue request and thread highlights. Live: compare plan.md with the current issue and contributor guidance. Good: one issue-sized change plus its tests; an explicit, reasoned deferral is acceptable. A rewrite or unrelated feature bundled with the fix is not bounded.

## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

Eval: look for a specific code area/file, chosen operation, and first implementation step in `## Candidate plan`, checked against any thread pointer. Live: read plan.md and the fork's files only to verify the named seam exists, not to supply missing steps. Good: another contributor can start at the named seam and knows what state or branch to change. “Investigate somewhere” or “choose whichever library later” does not give an executable direction.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

Eval: read the repro block's commands/input, before artifact and expected result, then the candidate plan's test. Live: compare the posted repro comment with plan.md's after-check and named regression test. Good: rerun the same trigger through the real affected code and predict a distinguishable after output or state, with relevant control coverage. “Run tests” alone and “feels faster” have no issue-specific oracle.

## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

Eval: compare the plan's asserted certainty, risks and unknowns with the repro and thread; any deviation described in the bundle belongs here. Live: read plan.md's risks/unknowns and `## Deviations` after build, comparing it to actual changed files if provided. Good: uncertainty is named with a bounded check; a truthful scoped-down plan passes. Do not demand a deviation before work has happened, but do not accept an unrecorded material change afterward.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

Eval: compare `## Candidate plan comment` with `## Thread highlights`, repo-facts policy/template and the candidate plan. Live: compare comment.md with the current issue conversation, contributor docs, and student's posted repro. Good: the comment conveys this student's diagnosis, bounded change and decisive test while responding to applicable maintainer guidance and prior work. Explicit mandatory AI-use disclosure requires the tool and extent in AI-assisted comments (the eval bundles are treated as AI-assisted); no disclosure requirement is inferred from mere AI-permissive or human-voice guidance. A classmate's claim or plan does not block an independent Path Review comment.
