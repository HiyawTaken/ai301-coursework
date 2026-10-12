# Unit 4 — Test and Submit

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/166

**Branch**

`fix/73-align-llm-env-example`

## Eval iterations

**Run history**

Full run 1: `agreement: 20/20 scored items  (bar: 18/20: PASS)`. This was the only full scored run. The saved, unedited final-run record is `beat-1-sandbox/unit-4/eval-run.txt`; every category met its floor.

**Package analysis**

`pkg-20`: my rubric decided **reject**; the gold label was **reject**. The Ghostty candidate gives a focused `Config.zig` diff, issue-specific before/after terminal-query evidence, and a passing `zig build test`. Those are strong on fidelity, test evidence, and diff quality. But its repo-facts block says, “All AI usage in any form must be disclosed, stating the tool used and the extent of the assistance”; the candidate description contains no such disclosure. Because the evaluation candidates are AI-assisted, the required repository-standards check fails despite the sound patch and tests.

**Check rationale**

The check quoted verbatim from my uploaded `tools/pr-precheck/rubric.md` is:

> | Repository standards and communication | Repo-facts template, contribution/AI policy and thread instructions compared with the candidate PR title/description, issue reference and any required file in the diff. | Meet explicit applicable template and contributor asks with real content, including issue linkage, required checklist or changelog file, and AI-use disclosure when the policy requires it. Eval candidates are AI-assisted; silence fails under an explicit disclosure rule. In live Path Review, include the course-required AI-use disclosure. A human-voice preference alone is not an AI-disclosure mandate. | required |

I wrote it to distinguish an actual repository requirement from a stylistic preference. The decisive source is the repo-facts policy or template, not whether a description merely sounds human or machine-written. That lets the check catch `pkg-20` without inventing a disclosure requirement for policy-silent repositories. Path Review additionally has the course's explicit disclosure instruction, which I fulfilled in PR #166's Notes for Reviewers.

**Trade-offs**

The standards rule gives up treating every unmentioned AI tool as an automatic hold. In a repository without an explicit AI-disclosure requirement, silence alone does not fail that check; a candidate could therefore be accepted even if I would personally prefer more attribution. That is intentional: the rubric judges the repository's stated standards, while other checks independently test plan fidelity, observable evidence, and truthful claims. The rule also permits a candidly disclosed unavailable check rather than equating a checked-off checklist with readiness. In my live PR, I left the CI and `make` boxes unchecked, named the unavailable command and its output, and reported the directly run pytest/ruff/mypy results.
