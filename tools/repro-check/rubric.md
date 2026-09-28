# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Issue-specific claim | Candidate claim comment read against the issue title and body, especially its concrete affected behavior. | The claim identifies this issue's particular behavior or affected surface, says what the writer will investigate or test next, and makes no unsupported promise of a fix, deadline, or assignment. A generic request to be assigned or a bare “same here” fails. | required |
| Reproducible environment | Repro report's OS/platform, relevant runtime or app versions, configuration/dependency/build profile, and tested code state (version, commit, or branch), read against the issue's targeted environment. | A stranger can identify the tested environment and code state and recreate the relevant conditions. A difference from the issue's target is stated and its effect considered; a silent version or platform mismatch fails. Name issue-relevant details, not every installed package. | required |
| Followable trigger | Repro report's setup, input/fixture, commands or UI actions, and starting state read against the issue's triggering steps. | An independent reader can reconstruct the input and follow the sequence from a stated starting state to the reported observation. The sequence actually exercises the issue's trigger; private files or unavailable configuration without a shareable equivalent fail. | required |
| Behavior evidence | The report's quoted output, error, log, screenshot description/link, measurement, or other artifact, compared with the issue's expected and reported actual behavior and any control run. | Artifacts show the particular behavior under discussion, or show an attempted trigger did not reproduce it. A banner, unrelated error, expected result alone, or assertion without an observation fails. A control helps when it distinguishes an adjacent symptom but is not mandatory. | required |
| Honest outcome | Report's stated observed result and expected result, any cannot-reproduce statement, causal explanation, and next step read against its artifacts and the issue context. | The conclusion says only what the artifacts establish. A faithful confirmed reproduction passes. An evidenced cannot-reproduce passes when it records the attempted trigger and relevant differences or limitations. A claimed crash over a noncrash artifact, unsupported root cause, or unacknowledged mismatch fails. | required |
| Repository communication rules | Repo-facts block's contribution policy, issue or PR templates, and AI-use requirements, compared with both candidate comments. In live mode, inspect the repository's contributor docs and issue thread. | Both comments meet explicit applicable requirements. This is an AI-assisted drafting and review workflow: if the repo requires disclosure of any AI use, each AI-assisted comment must state the tool and extent of assistance; an omitted disclosure fails even if the text does not otherwise reveal AI use. A repo with no such rule imposes no disclosure duty. The claim and report use their own specific observations, and neither substitutes boilerplate or a classmate's report for this writer's work. | required |

## Verdict rule

`accept` if every applicable required check passes. Any applicable `fail` or `unclear` means `reject`. In claim-only live mode, omit the four report-dependent checks (Reproducible environment, Followable trigger, Behavior evidence, Honest outcome) from the verdict, but still report them as `unclear` with `not yet applicable: claim-only draft`. There are no preferred checks.
