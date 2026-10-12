# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

1. Establish mode. Live: read scope.md first and stop on placeholder/wrong base repo; read voice-guide.md. Eval: use only the bundle. Read SKILL.md, rubric.md, this procedure and evidence guide before grading.
2. Read the issue, thread/maintainer direction and repo-facts policy/template first. Record the actual requested behavior and stated submission asks, so the PR cannot redefine them.
3. Read the accepted plan context next: repro, in/out scope, files, test plan and Deviations. List promised edits and expected observable after-results before viewing the diff.
4. Read the complete committed diff and commits, then test evidence, then title/description. In live mode obtain the diff with git diff main...HEAD, not the working tree; read plan.md, test_evidence.md and pr_draft.md. Do not grade until all artifacts have been read.

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides where the plan sits in the order (before the diff? before the
description?) and says why the order matters for the side-by-side
checks that come later. -->

## Evidence gathering

1. Pair every changed file and hunk with its plan item or deviation; also list plan items absent from the diff. Pair each description claim with an actual diff hunk or an explicit limitation.
2. Pair the plan's issue-specific trigger and expected after-state with the test-evidence commands and captured before/after. Mark a control-only or unchanged-path test separately from the actual failing path.
3. Extract each repo-required check from repo facts/template, then record its attempted command, output, result, or specific environmental barrier from test evidence. Never turn an unchecked box into a pass without the output.
4. Inspect the diff and commit context for debug residue, dead code, unrelated files, and formatting churn; quote a concrete hunk if present.
5. Compare title/description and any required changed file with template, contribution policy, AI rule and maintainer directions. Separate explicit disclosure mandates from mere human-voice preferences.

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which file, diff,
or page per your evidence guide) to pull the fact from, and what to
record. The load-bearing gathers this week are pairings: diff files
against plan scope, claimed evidence against the plan's test plan and
the repo's checks, description claims against diff contents. A
complete procedure leaves no check whose evidence an executor would
have to hunt for. -->

## Check execution

1. Execute rubric rows in order using the gathered pairs. Record pass, fail or unclear and one decisive artifact/quote for each row.
2. Fail when visible evidence contradicts a pass rule; mark unclear only when necessary evidence is genuinely absent. Do not repair a missing test, plan deviation or disclosure by inventing facts from the repository.
3. Apply honest-shortfall rules symmetrically: a documented deferral in the plan and description may pass fidelity, and an attempted check that fails with visible output may pass transparency. A hidden omission or unsupported success claim fails.
4. Reuse gathered evidence across checks but apply each row's separate condition. Do not replace outcome checks with style/length requirements. In live mode report voice-guide issues by rule name without changing unrelated rubric grades.

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

## Verdict assembly

1. Apply the binary rubric rule mechanically: all required passes yield accept; any fail or unclear yields reject. No averaging or “accept with reservations.”
2. In the readable summary quote the first failing required check in rubric order and its deciding diff/evidence/standard fact; mention other failures too and what would make them pass.
3. End with one valid fenced JSON block in the CONTRACT.md schema, all checks in rubric order, one-line evidence, then verdict. Emit nothing after its closing fence.

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check: the
check whose failure the verdict turned on. When more than one check
failed, your procedure picks which one gets quoted (first failing
required check in rubric order is a fine rule); nothing picks it for
you, so write the rule down. A complete procedure produces the same
verdict from the same grades, every time. -->
