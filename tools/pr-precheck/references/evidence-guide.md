# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift)

Eval: compare the plan-context scope pair, named files and deviations with every hunk of Candidate PR Diff, then compare title/description claims with the actual diff. Live: read plan.md including Deviations, git diff main...HEAD and pr_draft.md. Good: changes and omissions are inside the plan or a reasoned recorded deviation, and the description states exactly what shipped. A silently added flag/refactor or a promised docs update absent from the diff is drift even if tests pass.

<!-- Where the plan states its scope, boundary, and deviation notes,
and where the diff shows what actually changed. What it means for a
diff to match the plan, for an honest deviation to re-tie a mismatch,
and what silent drift looks like in each direction (more than the
plan, or less with no note). The description's fidelity claims read
against the diff live here too: a description claiming more or less
than the diff delivers is silent drift, not a comms problem. -->

## Test evidence (harness category: not-tested)

Eval: pair the plan-context repro and test plan with Candidate PR Test evidence, including commands, before/after, regression checks and named repository checks. Live: pair the student's posted Unit 2 repro and plan.md test plan with test_evidence.md and the Testing section of pr_draft.md. Good: the same failing path has an observable after-result, and required checks show real outcomes. A disclosed failure or unavailable check with command/output is honest evidence; “tests pass,” a control-only run or an unattempted check is not.

<!-- Where the PR shows its proof: the test-evidence section's
before/after against the plan's test plan and the reproduction's own
steps, and the outcome of the repo's own checks or suite. What
decisive looks like (an observable behavior named, the expected-after
stated, the checks' outcome visible) next to "tests pass". -->

## Diff quality (harness category: unreviewable)

Eval: inspect every unified-diff hunk and commits, not just the description. Live: git diff main...HEAD --stat and full diff plus git log main..HEAD. Good: the fix is isolated and reviewable, without debug prints, commented experiments, dead functions, unrelated formatting or drive-by edits. Commit wording alone does not replace reading the actual hunks.

<!-- Where the change itself lives: the unified diff and the commit
list. What a reviewable change looks like (the fix visible, nothing
unrelated riding along) and the debris tells: debug leftovers, dead
code, commented-out blocks, formatting churn, drive-by edits. -->

## Standards and comms (harness category: standards-wall)

Eval: compare repo-facts PR template, CONTRIBUTING/AI policy and thread highlights with Candidate PR title/description and any required changed file. Live: compare .github/PULL_REQUEST_TEMPLATE.md, docs/CONTRIBUTING.md and the issue thread with pr_draft.md and diff. Good: all applicable asks have substantive answers, issue linkage is correct and a required AI-use disclosure names tool and extent. Eval bundles are AI-assisted. Path Review also asks live students to disclose AI use in Notes for Reviewers. No generic disclaimer is required by a silent or merely human-voice policy.

<!-- Where the repo states its asks (the repo-facts block's PR
template sections, contributing instructions, and stated policy,
including AI-use disclosure) and where the PR honors them: the
stated sections filled with real content, the disclosure present,
explicit maintainer direction in the thread engaged. What compliant
looks like next to boilerplate or a visibly ignored ask. (Whether
the description's claims match the diff is plan fidelity, above.) -->
