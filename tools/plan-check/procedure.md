# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1. Determine mode. In live mode read `scope.md` first, reject an out-of-scope issue, then read `voice-guide.md`; in eval mode use only the supplied bundle and do not browse. Read this procedure, the full rubric, and the evidence guide before grading.
2. Read the issue title/body and thread highlights first. Record the requested behavior, any maintainer instruction, prior fix or test direction, and repository policy from the repo-facts block (live: issue thread and contributor docs). Do not let the candidate plan define the bug for you.
3. Read the repro-evidence block next (live: this student's posted repro comment). Record environment, exact trigger, before output, expected output, and control observations. These constrain which diagnoses and tests can pass.
4. Read the entire candidate plan, then the entire candidate plan comment. Record cause, change seam, inclusions/exclusions, implementation order, test oracle, risks, unknowns, and any deviation. Only after both drafts are understood, grade checks.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

1. For diagnosis and cause-directed change, pair each proposed causal claim and edit location with the repro observation or control that supports or rules it out. Record a contrary artifact explicitly instead of quoting only favorable lines.
2. For scope and executability, extract the plan's in/out boundaries, files or code areas, chosen mechanism, sequence, and gating decision; compare them with the issue request and any maintainer direction. Mark unrelated work separately from necessary regression coverage.
3. For the test plan, map each repro trigger and before artifact to the proposed post-fix action and predicted output/state. Check that it uses the real code path, and note whether a control or regression case is needed to distinguish adjacent failures.
4. For honesty, compare confidence, risks, unknowns, and Deviations text against the evidence and stated build state. In a pre-build plan, an empty future Deviations section is not itself a failure; after a build, compare any stated change with the original plan.
5. For communication, read the plan comment against the issue thread and repo-facts policy/template (live: contributor docs and current thread). Extract any explicit AI-disclosure rule separately from a human-written-voice preference. Compare comment promises with the plan; do not infer policy from a repo's silence.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Execute the rubric rows in table order using the gathered pairs. For each row, apply its pass condition to the candidate artifact and record `pass`, `fail`, or `unclear` plus one decisive quote or concrete fact.
2. Mark `fail` when present evidence contradicts the pass condition (for example, a control rules out the cause, a fix expands beyond the issue, or the test cannot observe the bug). Mark `unclear` only when the needed candidate evidence is genuinely absent. Do not rescue a missing plan with facts found only in the repo checkout or with a design you would write yourself.
3. A terse plan receives the same rule as a long one: do not require headings, a specific number of steps, or arbitrary test counts. A bounded hypothesis with a stated discriminating check can pass; unsupported certainty cannot.
4. If a check uses the same evidence as an earlier check, reuse the recorded quote but apply its separate pass condition. Do not skip any required row. In live mode also report voice-guide violations by rule name, without silently changing the rubric grade unless a rubric row covers them.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1. Apply the rubric's binary rule mechanically: `accept` only if every required row is `pass`; any `fail` or `unclear` yields `reject`. Do not average checks, and do not let an impressive test compensate for a wrong cause or ignored maintainer direction.
2. Before the final block, give a compact per-check summary. For every held check, quote the specific plan/repro/thread/policy fact that decided it and say what evidence or change would make the package ready.
3. End with exactly one fenced JSON object using the SKILL.md schema: issue URL or bundle id, all checks in rubric order with grades and one-line evidence, then the verdict. Emit nothing after the closing fence.
