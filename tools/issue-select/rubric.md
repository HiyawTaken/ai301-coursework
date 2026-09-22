# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
|  |  |  |  |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->
## Checks

| Check | Evidence to gather | Pass condition | Weight |
|---|---|---|---|
| Active stewardship | In an eval bundle, read `archived:`, the latest release, and the five default-branch commits, measuring dates against the capture date. In live mode, read the repository banner, latest release, and recent default-branch commits. | The repository is not archived **and** it has a human-authored default-branch commit within the last 180 days or a release within the last 365 days. Bot-only commits do not establish stewardship. | required |
| AI-compatible contribution policy | Read the contribution-policy line in an eval bundle or `CONTRIBUTING.md`, linked contributor docs, and dedicated AI-policy files in live mode. | Pass unless the policy expressly bans AI-generated or AI-assisted contributions. Requirements to disclose, test, understand, or review AI-assisted work pass because they are conditions to follow, not bans. Silence passes. | required |
| Available to take | Read the assignee and linked-PR facts, then the issue thread for a current maintainer-recognized claim or an in-progress contribution. In Path Review live mode, apply the house rule in `scope.md` to student claim comments. | There is no assignee, no open linked PR, and no current non-Path-Review claim or in-progress contribution in the thread. Closed or merged PRs and stale claim comments do not block the issue. | required |
| Bounded newcomer scope | Read the issue body and comments for the concrete change, named surfaces, acceptance criteria, maintainer decisions, and any abandoned attempts. | The issue identifies one implementable change in a defined feature area. A maintainer-filed or good-first-issue-labelled bug may be brief when its core behavior is identifiable. A finite set of related documentation updates, rule previews, possible root causes, or implementation alternatives for the same behavior still passes; these do not turn it into an umbrella. Fail an explicit umbrella/tracker issue, a pure usage question, an unresolved product/design decision, or an issue with repeated abandoned attempts showing that the apparent task is not actually bounded. | required |
| Newcomer signal | Read the issue labels and estimate stated in the body. | The issue has a `good first issue`/starter label, an explicit estimate of at most one workday, or a maintainer has identified the affected code and expected behavior. | preferred |

## Verdict rule

Accept only when every **required** check passes. Treat `unclear` as a failure for a required check. Preferred checks never affect the verdict; use them only to rank accepted live-mode candidates.
