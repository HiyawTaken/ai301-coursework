# Plan for issue #73: align the LLM environment example with setup guidance

## Diagnosis and evidence

My [Unit 2 reproduction](https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5863099313) used a clean checkout of my fork at `2f4e82f52efbcfcc57d65b3fa5348672163ca088`. After the documented `cp .env.example .env`, the files said:

```text
README.md:24:# Configure environment (add your OPENROUTER_API_KEY to .env)
docs/SETUP.md:47:# Edit .env and set your OPENROUTER_API_KEY (required for AI features)
.env:17:# Options: "mock" (default, no API key needed), "openai"
.env:18:LLM_PROVIDER=mock
.env:19:OPENAI_API_KEY=sk-your-key-here
OPENROUTER_API_KEY entry: absent from copied .env
loaded settings: llm_provider='mock', openrouter_key_present=False
control with temporary environment variable: openrouter_key_present=True
```

`core/config.py` defines `openrouter_api_key`, `openrouter_base_url`, and `openrouter_model`. The evidence supports a stale/incomplete example file and unclear Quick Start wording, not a demonstrated runtime failure or a proven provider-implementation defect.

## Scope and approach

Change only `README.md` Quick Start and `.env.example`. Clarify in the README that the default `mock` provider needs no key and that someone choosing OpenRouter should select it in `.env` and provide `OPENROUTER_API_KEY`. Update `.env.example`'s provider-options comment to include `openrouter` and add a blank `OPENROUTER_API_KEY=` field next to the existing OpenAI key. Keep `LLM_PROVIDER=mock` as the safe default and never put a real key in the repo.

I will first update the example, then the README, inspect the diff for unrelated edits, and rerun the copied-env check. I will not change `core/config.py`, provider wiring, dependency setup, or other configuration values; this issue asks for documentation/example agreement, and the repro did not establish a runtime failure.

## Test plan

1. Before the edit, from the fork root run the Unit 2 trigger in Git Bash: `cp .env.example .env`, then `grep -nE 'Options|LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY' .env` and check for `^OPENROUTER_API_KEY=`. The recorded before result lacks that entry and lists only `mock`/`openai`.
2. After the edit, repeat the same copy and grep. Pass means the copied `.env` has a blank `OPENROUTER_API_KEY=` entry, the options comment includes `openrouter`, and the README's Quick Start names the same key while still explaining that `mock` needs none.
3. In the existing Python venv, load `core.config.settings` from the copied `.env`; expect `llm_provider='mock'` and no OpenRouter key. As a control, set a temporary dummy `OPENROUTER_API_KEY` process variable and load settings again; expect the field to be populated. This proves the example is fillable and the loader reads the name, not that an external LLM call succeeds.
4. Review `git diff --check` and the changed-file list. No Docker or external API key is needed for this documentation/configuration check.

## Risks and unknowns

The repo has OpenRouter settings fields and an OpenRouter-capable generator, but I have not verified end-to-end selection via `LLM_PROVIDER=openrouter`. I will describe the configuration name the issue asks about without claiming an LLM call works. If the README needs more than a Quick Start clarification to stay accurate, I will record and explain that as a deviation before changing scope.

## Deviations

There was no change in scope or approach. I edited only `README.md` and `.env.example` as planned, kept `LLM_PROVIDER=mock` as the default, and reran the copied-env and settings-loader checks. I did not add provider-code changes or claim an end-to-end OpenRouter run.
