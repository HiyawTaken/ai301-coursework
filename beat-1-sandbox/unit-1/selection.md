# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73

**Verdict output**

All three candidates are collaborator-filed issues in the scoped repo
(`codepath/pathreview-ai301-fa26-s3`), with no assignees, no open PRs, and no
comments — no claims to worry about. The repo is active (a human-authored commit
five days ago), and `docs/CONTRIBUTING.md` says nothing about AI-assisted work, so
silence passes.

Ranked accepted candidates:

1. **#73** — README/`.env.example` key mismatch. Best fit: it is exactly the
   documentation/configuration fix with clear affected files in my profile:
   `good first issue` and `tier-1`, with a 1–2 hour estimate.
2. **#72** — `verify_password` should fail closed instead of raising. A contained
   Python change in `core/security.py` with an existing `xfail` test that states
   the expected behavior.
3. **#71** — Indented test fixture hides headings from the parser. A bounded,
   test-anchored Python fix, but it is `tier-2` and has no `good first issue`
   label, so it is a less newcomer-signaled choice.

None were rejected: no assignee, umbrella/design-debate, or policy blocker was
present.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
    "checks": [
      {"name": "Active stewardship", "grade": "pass", "evidence": "Repo not archived; latest default-branch commit 2026-09-16 by human author Andrew Burke, 5 days before today (2026-09-21)"},
      {"name": "AI-compatible contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md contains no AI restriction; silence passes"},
      {"name": "Available to take", "grade": "pass", "evidence": "assignees: [] and comments: 0; repo has zero open PRs"},
      {"name": "Bounded newcomer scope", "grade": "pass", "evidence": "Body names two files (README.md, .env.example) and the exact fix: 'Make the two files agree'"},
      {"name": "Newcomer signal", "grade": "pass", "evidence": "Labels: good first issue, tier-1; 'Estimated effort: 1–2 hours'"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
    "checks": [
      {"name": "Active stewardship", "grade": "pass", "evidence": "Same repo-level facts: not archived, human commit 5 days ago"},
      {"name": "AI-compatible contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md silent on AI use"},
      {"name": "Available to take", "grade": "pass", "evidence": "assignees: [] and comments: 0; no open PRs in repo"},
      {"name": "Bounded newcomer scope", "grade": "pass", "evidence": "Body names core/security.py and tests/unit/test_security.py, with a covering xfail test (H-05) defining expected behavior"},
      {"name": "Newcomer signal", "grade": "pass", "evidence": "Labels: good first issue, tier-1; 'Estimated effort: 1–2 hours'"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/71",
    "checks": [
      {"name": "Active stewardship", "grade": "pass", "evidence": "Same repo-level facts: not archived, human commit 5 days ago"},
      {"name": "AI-compatible contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md silent on AI use"},
      {"name": "Available to take", "grade": "pass", "evidence": "assignees: [] and comments: 0; no open PRs in repo"},
      {"name": "Bounded newcomer scope", "grade": "pass", "evidence": "Body names tests/unit/test_readme_parser.py and ingestion/parsers/readme_parser.py with the exact fix: 'Remove the indentation'; covering xfail test (H-04)"},
      {"name": "Newcomer signal", "grade": "pass", "evidence": "No good-first-issue label (bug, ingestion, tier-2), but 'Estimated effort: 1–2 hours' satisfies the ≤1-workday condition"}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

**Run history**

The first usable smoke check recorded `agreement: 1/1 scored items` for
`issue-02`. The first complete run recorded `agreement: 17/20 scored items
(bar: 18/20: below the bar)`. I then ran the changed-scope canaries and recorded
`agreement: 3/3 scored items`. The confirming complete run recorded
`agreement: 19/20 scored items  (bar: 18/20: PASS)`. Before the smoke check, a
Windows launcher attempt did not produce a score because the harness could not
invoke the npm `claude.cmd` shim; that was a platform setup failure, not a rubric
verdict.

**Issue analysis**

I analyzed `issue-01`. The confirming transcript records `issue-01  accept
accept   yes`, so my rubric decided **accept** and the gold label was also
**accept**. Its proposed permanent documentation page and related updates are a
finite group around one feature, rather than a tracker. The deciding language in
my rubric is: “A finite set of related documentation updates, rule previews,
possible root causes, or implementation alternatives for the same behavior still
passes; these do not turn it into an umbrella.” That is why the change from the
first run did not make broad, unrelated work acceptable.

**Check rationale**

Quoted check wording: “The issue identifies one implementable change in a defined
feature area. A maintainer-filed or good-first-issue-labelled bug may be brief
when its core behavior is identifiable. A finite set of related documentation
updates, rule previews, possible root causes, or implementation alternatives for
the same behavior still passes; these do not turn it into an umbrella. Fail an
explicit umbrella/tracker issue, a pure usage question, an unresolved
product/design decision, or an issue with repeated abandoned attempts showing
that the apparent task is not actually bounded.”

I chose this wording because an issue description can list several closely related
edits while still giving a newcomer one coherent result to implement and test. It
also keeps the important boundaries explicit: tracking lists, undecided product
work, and a history of abandoned attempts are evidence that a task only looks
small on the surface.

**Trade-offs**

The first full run recorded `issue-01  accept  reject   NO     failed: Bounded
newcomer scope`, and the targeted re-check later recorded `issue-01  accept
accept   yes`. The revised check intentionally gives up the stricter rule that a
multi-file documentation request must fail. Its counterweight is the phrase
“one implementable change in a defined feature area”: the same final run still
records `issue-10  reject  reject   yes` for the self-described megaissue.

---

## Selection rationale

**Selection rationale**

1. Issue #73 fits my stated interest in documentation and configuration work. It
   names only `README.md` and `.env.example`, gives an exact inconsistency to
   resolve, and estimates 1–2 hours, which makes it realistic for the Unit 2
   window.
2. The verdict correctly identified an active repo, an AI-compatible policy, no
   current claimant, and a bounded two-file change. Beyond the rubric, I weighed
   that the change should be easy to verify by comparing the setup instructions
   with the example configuration and making sure the documentation does not
   imply that a real API key belongs in the example file.
3. Claiming should be low difficulty: the live run found no assignee, no open
   pull request, and no comments. I will still follow the Unit 2 claim process
   and will not comment until that unit instructs me to do so.
