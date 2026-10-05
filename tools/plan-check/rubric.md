# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Evidence-grounded diagnosis | The issue's symptom and repro-evidence block (including controls), compared with the candidate plan's stated cause or causal hypothesis. | The diagnosis explains the distinguishing observation without contradicting a repro control. A plausible, explicitly testable hypothesis passes when the evidence cannot prove the cause; a cause ruled out by the evidence or an assertion with no issue-specific support fails. | required |
| Cause-directed change | The repro's failure point and any maintainer diagnosis in thread highlights, compared with the plan's proposed intervention and affected code path. | The proposed change acts at a plausible source of the reproduced behavior, or names a verification step before choosing between bounded candidate sources. Merely masking the visible symptom while leaving the evidenced cause untouched, or deferring every implementation decision, fails. | required |
| Bounded scope | The plan's in-scope and out-of-scope change, named files/areas, and issue request, compared with the repro and thread. | The work is one coherent fix for the issue, with related regression coverage. Unrelated refactors, migrations, new features, or broad redesigns bundled as prerequisites fail; a narrower defensible fix with an explicit deferral passes. | required |
| Executable approach | The plan's files or code areas, chosen mechanism, work order, and any specific unknown that gates an edit. | Another contributor can identify where to start and what change to attempt without first inventing the design. A short plan can pass; “investigate/optimize somewhere” with no chosen seam or decision rule fails. | required |
| Decisive test plan | The repro-evidence block's trigger, before artifact and expected behavior, compared with the plan's proposed commands/fixtures and expected after observation. | The test re-exercises the real affected path and specifies an observable pass/fail result that distinguishes the fix from the original failure. A generic test-suite run, subjective “looks good,” or a test that never triggers the bug fails. Add a relevant control or regression case when the repro uses one to isolate the cause. | required |
| Honest uncertainty and deviations | The plan's confidence language, risks, unknowns and Deviations note, compared with repro evidence and any build changes stated in the package. | Claims stay within the shown evidence; material unknowns have a bounded way to resolve them before coding or testing. A recorded, explained deviation passes; an unacknowledged contradiction, claimed certainty over a disproven cause, or a crucial choice deferred indefinitely fails. | required |
| Thread-aware communication | The candidate plan comment compared with issue thread highlights, maintainer direction, repo-facts contribution policy/templates and AI-use rules, plus the plan's own scope and test. | The comment describes this plan's concrete change and verification, responds to applicable maintainer direction or prior work, and obeys explicit repo conventions. In this AI-assisted grading workflow, a repo that requires disclosure of any AI help must see the tool and extent disclosed; absent disclosure then fails. No disclosure duty is inferred from silence or a merely human-voice rule. A classmate's parallel plan does not block an independent Path Review plan. | required |

## Verdict rule

Return `accept` only when every required check passes. Return `reject` if any required check fails or is `unclear`; missing evidence is not a guessed pass. There are no preferred checks. Grade the candidate plan and comment on what they actually say, not their length, heading format, or rhetorical polish.
