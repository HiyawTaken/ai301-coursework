# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

## Posted upstream

**GitHub username**

HiyawTaken

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5987549084

I reproduced #73 in my fork at `2f4e82f`: after `cp .env.example .env`, the README asks for `OPENROUTER_API_KEY`, but the copied example lists only `mock`/`openai` and `OPENAI_API_KEY`; `core/config.py` has an OpenRouter key field. I plan a bounded documentation/example fix in `README.md` and `.env.example`: clarify when a key is needed, list `openrouter` as an option, and add a blank `OPENROUTER_API_KEY=` entry while keeping `mock` the default. I’ll rerun the copied-env grep and settings-loader check with a dummy key to show the before/after. This plan does not claim that OpenRouter works end-to-end or change provider code.

## Your branch

**Branch**

`fix/73-align-llm-env-example` — [branch in my fork](https://github.com/HiyawTaken/pathreview-ai301-fa26-s3/tree/fix/73-align-llm-env-example), commit `69b7833` authored by HiyawTaken. The branch commit contains only `README.md` and `.env.example`; `plan.md` and `comment.md` stayed out of it.

**Evidence**

The same copied-environment trigger from my Unit 2 repro was run before and after the change. No real key was used.

Before — fork `main` at `2f4e82f`, Git Bash from the repo root:

```bash
cp .env.example .env
grep -n "OPENROUTER_API_KEY" README.md docs/SETUP.md
grep -nE "Options|LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY" .env
if grep -q "^OPENROUTER_API_KEY=" .env; then echo "BEFORE: OpenRouter entry present"; else echo "BEFORE: OpenRouter entry absent"; fi
```

```text
README.md:24:# Configure environment (add your OPENROUTER_API_KEY to .env)
docs/SETUP.md:47:# Edit .env and set your OPENROUTER_API_KEY (required for AI features)
17:# Options: "mock" (default, no API key needed), "openai"
18:LLM_PROVIDER=mock
19:OPENAI_API_KEY=sk-your-key-here
BEFORE: OpenRouter entry absent
```

Before — PowerShell, using the existing `.venv/Scripts/python.exe` and a temporary dummy process variable as a control:

```powershell
& '.\.venv\Scripts\python.exe' -c "from core.config import settings as s; print(f'BEFORE: llm_provider={s.llm_provider!r}, openrouter_key_present={bool(s.openrouter_api_key)}')"
$env:OPENROUTER_API_KEY='unit3-test-only'
& '.\.venv\Scripts\python.exe' -c "from core.config import settings as s; print(f'BEFORE control: openrouter_key_present={bool(s.openrouter_api_key)}')"
Remove-Item Env:OPENROUTER_API_KEY
```

```text
BEFORE: llm_provider='mock', openrouter_key_present=False
BEFORE control: openrouter_key_present=True
```


After — branch `fix/73-align-llm-env-example` at `69b7833`, the same Git Bash commands:

```bash
cp .env.example .env
grep -n "OPENROUTER_API_KEY" README.md docs/SETUP.md
grep -nE "Options|LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY" .env
if grep -q "^OPENROUTER_API_KEY=" .env; then echo "AFTER: OpenRouter entry present"; else echo "AFTER: OpenRouter entry absent"; fi
```

```text
README.md:26:# To use OpenRouter, set LLM_PROVIDER=openrouter and OPENROUTER_API_KEY in .env
docs/SETUP.md:47:# Edit .env and set your OPENROUTER_API_KEY (required for AI features)
17:# Options: "mock" (default, no API key needed), "openai", "openrouter"
18:LLM_PROVIDER=mock
19:OPENAI_API_KEY=sk-your-key-here
20:# For OpenRouter, set LLM_PROVIDER=openrouter and fill in this key.
21:OPENROUTER_API_KEY=
AFTER: OpenRouter entry present
```

After — the same settings-loader and dummy-key control:

```powershell
& '.\.venv\Scripts\python.exe' -c "from core.config import settings as s; print(f'AFTER: llm_provider={s.llm_provider!r}, openrouter_key_present={bool(s.openrouter_api_key)}')"
$env:OPENROUTER_API_KEY='unit3-test-only'
& '.\.venv\Scripts\python.exe' -c "from core.config import settings as s; print(f'AFTER control: openrouter_key_present={bool(s.openrouter_api_key)}')"
Remove-Item Env:OPENROUTER_API_KEY
```

```text
AFTER: llm_provider='mock', openrouter_key_present=False
AFTER control: openrouter_key_present=True
```

This demonstrates that the copied example now contains the missing fill-in field and names the same provider as the README while retaining the safe `mock` default. It does not claim an external OpenRouter request was tested.

## Eval iterations

**Run history**

1. A preflight harness invocation reached no packages because Claude Code's OAuth session had expired (0/0 scored; it wrote no submission run). I renewed the session and reran.
2. First complete scored run: **20/20** agreement; all five categories matched.
3. Confirming complete run with `--save-run eval-run.txt`: **20/20** agreement; clear-accept 7/7, scope-creep 4/4, thread-convention 2/2, unbuildable 3/3, wrong-cause 4/4. This final score matches the unedited harness file submitted alongside this write-up.

**Package analysis**

For scored `pkg-20` (Ghostty), my rubric decided **reject** and the gold label was **reject**. The plan itself is bounded and testable, but the repo-facts block explicitly requires disclosure of any AI assistance and the candidate plan comment contains none. The `Thread-aware communication` check therefore fails even though the other plan checks pass. The eval set treats candidate work as AI-assisted, so silence does not satisfy Ghostty's stated policy.

**Check rationale**

The uploaded `rubric.md` says exactly:

```text
| Thread-aware communication | The candidate plan comment compared with issue thread highlights, maintainer direction, repo-facts contribution policy/templates and AI-use rules, plus the plan's own scope and test. | The comment describes this plan's concrete change and verification, responds to applicable maintainer direction or prior work, and obeys explicit repo conventions. In this AI-assisted grading workflow, a repo that requires disclosure of any AI help must see the tool and extent disclosed; absent disclosure then fails. No disclosure duty is inferred from silence or a merely human-voice rule. A classmate's parallel plan does not block an independent Path Review plan. | required |
```

I kept this as a required outcome check because a plan comment is part of what gets posted: a technically sound plan can still disregard a maintainer's instruction or a repo's explicit contribution policy. The wording separates mandatory disclosure from mere silence or a human-voice preference, and Path Review's parallel-classmate rule means an independent plan is still valid on a shared issue.

**Trade-offs**

This check rejects the otherwise strong `pkg-20` because its comment lacks the explicitly required disclosure; it also rejects `pkg-04`, where a docs-only plan comment ignores the maintainer's requested test of an isolated code fix. It does **not** reject `pkg-03` merely for lacking an AI disclaimer: that repo asks for human-written comments but does not impose the same disclosure rule. Both full runs agreed on all three of these cases, so the boundary did not flip elsewhere in the scored set.
