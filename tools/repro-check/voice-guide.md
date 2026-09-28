# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

I am a student contributor using this repo to learn a careful open source workflow. I can test a specific behavior, record what happened, and share a report another person can run. I do not speak for maintainers or promise a fix before I understand the problem.

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.

Format each rule like this:

### Rule: <short name>

<The rule, one or two sentences.>

- Wrong: "<a line that breaks it>"
- Right: "<the line to post instead>"
-->

### Rule: Name the actual issue

In a claim, mention the affected file or behavior and the action I plan to test so the comment could not be pasted onto another issue unchanged.

- Wrong: "Please assign me this issue; I will work on it."
- Right: "I will compare the README setup steps with `.env.example` for issue #73, then report what a fresh setup actually requires."

### Rule: Promise an investigation, not a fix

Before reproduction, state the next check and promise a report, without a date, guaranteed patch, or claim that I already verified it.

- Wrong: "I confirmed the cause and will fix this by tomorrow."
- Right: "I will check the documented configuration against the example file and post the result here."

### Rule: Show the evidence I used

When reporting, include the tested code state, commands or UI actions, and decisive output. Keep observations separate from interpretations.

- Wrong: "The setup is broken because the config is wrong."
- Right: "At commit `<sha>`, `README.md` asks for `OPENROUTER_API_KEY`; `.env.example` does not list it. I observed the mismatch in the two files."

### Rule: Say exactly what happened

If the behavior does not reproduce, say so and name the conditions; do not turn a plausible explanation into a proven cause.

- Wrong: "The missing variable definitely causes every startup failure."
- Right: "I reproduced the documentation mismatch; I have not established that it causes a startup failure."

### Rule: Credit only my own attempt

Even if another student posted a report, describe my own environment and result rather than leaning on their conclusion.

- Wrong: "Same as above, confirmed."
- Right: "In my checkout at `<sha>`, I compared the README instructions with `.env.example` and found the following difference: ..."

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->

- A guaranteed fix, delivery date, or request for ownership before reproducing.
- A root-cause claim that my commands and output do not support.
- Real API keys, tokens, or private `.env` contents.
- “Same as above” as a substitute for my own report.
