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

experience level： entry level software engineer

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

### Rule: Evidence before claims
I only point out what I discovered, not suspect without evidence.
- Wrong: I confirmed the root cause
- Rtight: I looked into SafetyMonitor.get_event_count() and found ...

### Rule: Promise investigation, not a fix
Before I have reproduced the bug, I only promise to look into it and report back. I never promise a fix or a date.
- Wrong: "I'll fix this by Friday."
- Right: "I'll reproduce this on main and post what I find here.
  
### Rule: Name the specific thing
Every comment mentions something only this issue has: the endpoint, field, file, or function.
- Wrong: "I'd like to work on this issue."
- Right: "I'd like to look into why `/health` always returns `safety_events_last_hour: 0`, starting from `SafetyMonitor.get_event_count()`."


## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->

"I'll fix this by Friday" -- (x)
"Sorry I'm just a beginner" -- (x)