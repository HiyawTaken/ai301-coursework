---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

Answer exactly one question: is this candidate pull request ready to submit? Compare its committed diff, title, description, and test evidence with the accepted issue plan (including deviations), repro, issue thread, and applicable repository standards. Do not treat a persuasive description as proof that the diff or tests match it.

<!-- State, in your words, the one question this tool answers and what
a PR package is: what artifacts it contains and what they are read
against. CONTRACT.md fixes the question; your frame has to say it so
the tool cannot wander into grading something else. -->

## Inputs and modes

Live mode: read the named plan.md including Deviations, pr_draft.md (first line title; rest description), test_evidence.md, the full committed branch diff from git diff main...HEAD (three dots), and its commits. Read the issue URL's body, thread, this student's posted repro and plan comment, and the repo's .github/PULL_REQUEST_TEMPLATE.md and docs/CONTRIBUTING.md. Do not silently include uncommitted edits as PR changes. For a house chain, use the supplied house plan and repro pack. The draft package, not facts hidden in other files, must carry the proof a reviewer needs.

Eval mode: the single frozen bundle is the whole world. Read its repo facts, issue/thread, plan context, candidate title/description, commits, diff, and test evidence; fetch nothing and do not inspect the live repository. Grade every rubric check and apply the full verdict rule.

<!-- Define both modes. Live mode: name every input (your plan.md with
its deviation notes, your branch's diff, your draft PR title and
description, your test evidence, your issue), where each comes from,
and what a house-chain student reads instead. The branch's diff is
everything the branch changes relative to the repo's default branch:
`git diff main...HEAD` (three dots), run from the working copy, is
the command that produces it; name the source that concretely. Eval
mode: state that the bundle is the whole world, nothing is fetched,
and every check runs with the full verdict rule. -->

## The scope seam (live mode only)

Read scope.md before gathering live evidence. Refuse to grade if its Repo line is a placeholder, or if the intended base repository, issue, or posted plan is outside that scoped Path Review repo. Apply its house rules: own fork/issue branch, one PR per student per issue, template, and independent work even when classmates have PRs. In eval mode ignore scope.md entirely.

<!-- Tell the tool when to read scope.md, what to do with the rules it
finds there, what to refuse, and what to do when the scope's repo line
is an unfilled placeholder. State that eval mode ignores scope.md
entirely. CONTRACT.md names the required behavior; your frame has to
instruct it. -->

## The voice seam (live mode only)

Read voice-guide.md in live mode and compare both outgoing title and description with its rules; name and quote any broken rule in the summary. Voice does not alter a rubric verdict unless a rubric check independently covers it. Ignore the voice guide in eval mode.

<!-- Tell the tool when to read voice-guide.md, which outgoing text it
gates (the PR title and description), how to report a broken rule, and
why it never changes the verdict on its own. State that eval mode
ignores it entirely. -->

## Component reads

Read rubric.md for the named checks and binary verdict rule, references/evidence-guide.md for each check's precise source, then execute procedure.md in order. If rubric checks or procedure steps are empty, refuse to grade and explain why. If the procedure is silent about a needed move, report the gap rather than inventing a step. Template comments are not filled content.

<!-- Tell the tool how the pieces connect: rubric.md defines the
checks and the verdict rule, references/evidence-guide.md maps where
each evidence family lives, procedure.md is executed as written. Say
what the tool does when the procedure is silent on a step (report the
gap, never improvise around it) and what it does when rubric.md or
procedure.md has no content (the refusal rule, stated as an
instruction). -->

## Verdict and output

Return only accept (ready to submit) or reject (hold) by the rubric's rule. A short per-check summary may precede the JSON, but end with exactly the following valid fenced JSON block and nothing after it. Include all checks in rubric order and one decisive evidence fact per grade.

<!-- State the binary verdict space (accept means submit, reject means
hold) and instruct the tool to end its reply with the fenced JSON
block below, valid and last, with nothing after it. The schema is
CONTRACT.md's, verbatim; do not edit it. -->

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

For every grade cite the fact or artifact that decides it. Grade the actual diff, outcomes, and stated standards rather than prose polish or length. Apply the rubric even if intuition differs; fix a poor rule in the rubric, not in one run. Follow the procedure exactly and expose its gaps. If a needed fact is absent, mark its check unclear; when the rubric is silent, unclear counts as failure. An honestly disclosed shortfall may pass if plan/deviation and description agree and the attempted test plus limitation are observable; unsupported success claims do not.

<!-- Write the standing rules the tool grades under: evidence first,
grade the thing not the polish, the rubric decides, the procedure
decides how, and how unclear grades are treated when the rubric's
verdict rule is silent. CONTRACT.md states each as a guarantee; your
frame has to make them instructions. -->
