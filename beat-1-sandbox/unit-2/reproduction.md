# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

## Your identity upstream

**GitHub username**

HiyawTaken

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5863052199

I’d like to investigate #73. I’ll follow the documented environment setup in a fresh checkout, compare the README’s `OPENROUTER_API_KEY` instruction with `.env.example` and `core/config.py`, and post the commands, environment, and observed result here. If the mismatch is no longer present, I’ll report that honestly instead.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5863099313

## Reproduction report for #73

I reproduced the README / `.env.example` configuration mismatch in my own fork.

**Environment and code state:** Windows 11 Home 10.0.26200 (64-bit), Git 2.50.1.windows.1, Python 3.13.6. I cloned `HiyawTaken/pathreview-ai301-fa26-s3` at commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088` (`main`, clean tracked worktree). In line with the Windows setup guidance, I used Git Bash for the documented `cp` step and file checks. I created a `.venv` and installed `pydantic-settings` to load `core.config`; no real API key was used.

**Steps and output** (from the repository root):

```bash
cp .env.example .env
grep -n 'OPENROUTER_API_KEY' README.md docs/SETUP.md
grep -nE 'Options|LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY' .env
if grep -q '^OPENROUTER_API_KEY=' .env; then echo 'entry present'; else echo 'OPENROUTER_API_KEY entry absent from copied .env'; fi
```

```text
README.md:24:# Configure environment (add your OPENROUTER_API_KEY to .env)
docs/SETUP.md:47:# Edit .env and set your OPENROUTER_API_KEY (required for AI features)
17:# Options: "mock" (default, no API key needed), "openai"
18:LLM_PROVIDER=mock
19:OPENAI_API_KEY=sk-your-key-here
OPENROUTER_API_KEY entry absent from copied .env
```

I then checked the settings declaration and loaded the copied `.env` in the venv:

```text
core/config.py:18:llm_provider: str = Field(default="mock")
core/config.py:19:openai_api_key: str = Field(default="")
core/config.py:20:openrouter_api_key: str = Field(default="")
core/config.py:21:openrouter_base_url: str = Field(default="https://openrouter.ai/api/v1")
loaded settings: llm_provider='mock', openrouter_key_present=False
control with temporary environment variable: openrouter_key_present=True
```

The loader output came from `python -c "from core.config import settings as s; print(f'loaded settings: llm_provider={s.llm_provider!r}, openrouter_key_present={bool(s.openrouter_api_key)}')"` using `.venv/Scripts/python.exe`. For the control, I set a temporary process environment variable to the dummy value `unit2-test-only` and ran the same import; I printed only whether the key was present.

**Expected:** the example copied by the README's setup step should include an `OPENROUTER_API_KEY` entry to fill in and list the corresponding provider option, consistent with the README, setup guide, and configuration fields.

**Observed:** the copied `.env` contains only the `mock`/`openai` option comment and `OPENAI_API_KEY`; it has no `OPENROUTER_API_KEY` entry. The settings loader leaves the OpenRouter key empty until a value is supplied separately. This confirms the documentation/example mismatch, not a claim that OpenRouter fails at runtime.

**Limit:** I did not start the app or call an LLM. Docker Desktop's engine was unavailable (`docker info` could not connect), so database/migration and full `make setup` steps were not run. Those services are not needed to observe this file-and-settings mismatch.

## Eval iterations

**Run history**

1. First full run: **19/20** agreement. The disclosure category was **0/1**, so the category floor was unmet and the run did not pass. The lone disagreement was `pkg-20`: my rubric accepted a Ghostty package whose AI-assisted comments omitted the disclosure required by that repository.
2. Revised the repository-communication check and evidence guide. A targeted `--only pkg-20,pkg-19` run scored **2/2**: `pkg-20` flipped to the correct reject, and `pkg-19` remained reject. This partial run was diagnostic, not a bar result.
3. Confirming full run, written unedited by the harness to `eval-run.txt`: **19/20** agreement, with clear-accept 7/8, disclosure 1/1, no-evidence 4/4, unfollowable-comms 3/3, and wrong-target 4/4. The 18/20 bar and every category floor passed. The remaining disagreement was `pkg-03`.

**Package analysis**

On scored `pkg-20` (Ghostty mode-2031 report), the final rubric decided **reject**, and the gold label was **reject**. The environment, trigger, and observed light-vs-dark escape-sequence evidence were sufficient, but Ghostty's captured policy requires disclosing *any* AI assistance by tool and extent. The candidate claim and report omitted that disclosure. The first full run had incorrectly accepted it by treating silence as evidence of no AI use; the revised check makes this AI-assisted workflow explicit and catches the omission.

**Check rationale**

The uploaded `rubric.md` check reads exactly:

```text
| Repository communication rules | Repo-facts block's contribution policy, issue or PR templates, and AI-use requirements, compared with both candidate comments. In live mode, inspect the repository's contributor docs and issue thread. | Both comments meet explicit applicable requirements. This is an AI-assisted drafting and review workflow: if the repo requires disclosure of any AI use, each AI-assisted comment must state the tool and extent of assistance; an omitted disclosure fails even if the text does not otherwise reveal AI use. A repo with no such rule imposes no disclosure duty. The claim and report use their own specific observations, and neither substitutes boilerplate or a classmate's report for this writer's work. | required |
```

I changed this from a generic "follow AI-use disclosure when required" condition after the first run misgraded `pkg-20`. The new outcome rule identifies the specific required content (tool and extent) and says silence fails under an explicit disclosure policy. It also says a repo without such a policy creates no disclosure duty, so the check is not a universal demand for an AI disclaimer.

**Trade-offs**

The stricter wording caught `pkg-20`, and `pkg-19` stayed correct in the targeted canary run. It also led the confirming grader to reject `pkg-03` (ripgrep), which gold accepts: that repo asks for comments in a human's own words but does not explicitly require AI-use disclosure. All of `pkg-03`'s issue, environment, trigger, and behavior-evidence checks passed; the grader overread the human-words policy as a disclosure rule. I kept the check because the assignment's single mandatory-disclosure case otherwise escapes, and I am recording this false-reject boundary rather than hiding it.
