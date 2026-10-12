# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan-to-diff fidelity | Plan-context scope, named files, exclusions and deviations compared with the candidate commits and every changed diff hunk. | Each functional change implements the plan or an explicit, reasoned deviation; each promised change is present or an explicitly deferred shortfall. Silent additions and silently missing work fail, even when the core fix is sound. | required |
| Description-to-diff truth | Candidate title, summary, changes, issue link and claimed limitations read against the diff, plan and deviation note. | A reviewer can tell what the committed branch actually changes and does not change. Claims of an absent feature, claimed exact fidelity over extra hunks, or undisclosed omitted work fail; a candid scoped-down result passes. | required |
| Decisive issue evidence | Plan-context repro and test plan compared with the candidate test-evidence section's commands, inputs, before/after output and any added test. | Evidence exercises the issue's distinguishing failing path through the changed code and shows an observable before/after or an honestly evidenced limitation. A control-only run, generic success claim, or test of an unchanged adjacent path fails. Where the accepted plan deliberately defers a case, test the delivered case and disclose the deferral. | required |
| Repository check outcomes | Repo-facts required checks or candidate PR template checklist compared with the test-evidence section and testing claims. | The applicable checks were attempted and their actual outcomes shown, or an environmental inability is named with the attempted command, output and consequence. Unsupported checked boxes, silent omission of required checks, or “all tests pass” without named results fails. A disclosed failing or unavailable check is not automatically a failed PR. | required |
| Reviewable diff | Unified diff and commit list, including context around changed hunks, compared with the issue-sized fix. | The intended fix can be reviewed without debug prints, dead/commented-out experiments, unrelated edits, or material formatting churn. Terse commits or a small adjacent hunk do not fail by themselves; debris that obscures the change does. | required |
| Repository standards and communication | Repo-facts template, contribution/AI policy and thread instructions compared with the candidate PR title/description, issue reference and any required file in the diff. | Meet explicit applicable template and contributor asks with real content, including issue linkage, required checklist or changelog file, and AI-use disclosure when the policy requires it. Eval candidates are AI-assisted; silence fails under an explicit disclosure rule. In live Path Review, include the course-required AI-use disclosure. A human-voice preference alone is not an AI-disclosure mandate. | required |

## Verdict rule

Return accept only when every required check passes. Return reject if any required check fails or is unclear; absent evidence is not guessed into a pass. There are no preferred checks. Grade the outcome and its honest limits, not the length, headings, number of commits, or confidence of the prose.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->
