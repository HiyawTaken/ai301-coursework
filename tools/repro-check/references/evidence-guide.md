# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

In an eval bundle, read the issue context's platform/version target and the repo-facts block, then find the actual OS, version or commit, runtime, configuration, and build profile in the candidate repro report. In live mode, compare the issue page and contributor setup docs with the report draft; the current checkout alone is not evidence to the future reader unless the report names it. Good: the reader can recreate the conditions that matter to this issue and see any difference between the reporter's setup and the issue target. A silent old-version or platform substitution cannot establish the reported bug.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

In eval mode, read the issue's triggering action and the report's setup, fixture contents, commands, and action sequence. In live mode, use the issue body and the draft comment, not an unshared local file. Good: a stranger can start from a known state, reconstruct any input, run the same trigger, and observe the result. Private workspaces, unspecified flags or drivers, missing fixture contents, and a command that tests a different operator or argument form fail even when the report is polished.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

Locate the issue's expected and reported actual behavior in the issue context. Then read the report's pasted output, exit status, log excerpt, screenshot or measurement, and any comparison/control. The artifact must exhibit the same distinguishing symptom, or document a real attempt in which that symptom did not occur. A version banner, a successful launch, or a different error is not proof of a crash, blank pane, or malformed output. In live mode, the artifact must be included or linked in the posted draft so a reader need not inspect the student's machine.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

Compare the claim and report's certainty, diagnosis, and expected/actual statements to the artifacts and the issue. Good: “I observed X under Y conditions,” or “I could not reproduce after these steps; my setup differs in Z,” when those observations are shown. A plausible hypothesis may be labelled as a hypothesis. Unsupported assertions that a race or crash is confirmed, or generalizations to untested platforms, fail. A cannot-reproduce with actual attempted steps and output is a valid outcome.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

In eval mode, compare the candidate claim and report with the issue specifics and the repo-facts block's contributor policy, template asks, and AI-use rule. In live mode, inspect the repository's CONTRIBUTING and linked policy/template files and the issue thread, then compare both drafts. Good: the claim names the specific issue behavior and commits only to an investigation and a report; the repro presents this author's own work. This skill participates in AI-assisted drafting/review, so where a repo requires disclosure of any AI use, check that each assisted comment actually names the tool and extent of assistance; do not infer "no AI use" merely because the candidate is silent. A repo with permissive policy or no policy creates no extra disclosure requirement. Do not claim a deadline, guaranteed fix, or ownership that the evidence cannot support. Path Review's scope allows parallel classmates but still requires an independent report.
