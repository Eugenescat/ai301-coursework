# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->
Used by: env-recorded

where:
- Candidate repro report: the environment line (OS, tool and dependency versions, code state such as a release or commit).
- Read it against: the versions and platform named in the Issue body, and Repo facts: latest release.
- Thread highlights: which versions or platforms a maintainer or other reporter confirmed (or could not reproduce on).

under live mode: the environment section of my draft, read against the issue body and thread on GitHub and the repo's README / CONTRIBUTING.md setup instructions.

good looks like: the report names the OS and the versions of everything the issue depends on (e.g. the tool, the runtime, any dependency the thread suspects). If the version or platform differs from what the issue targets, the report says so in its own words ("filed against 13.0.0;tested on 15.2.0"). A different version used silently is a fail, even when every other field is filled in. No environment record at all is a fail, even when the output looks right.


## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->
Used by: steps-followable

where:
- Candidate repro report: the steps / commands and any input files or configs they use.
- Read them against: the trigger the Issue describes (its own steps, input, flags, platform-specific options).
- Thread highlights: extra trigger conditions a maintainer added.

under live mode: the steps in my draft, read against the issue body and thread on GitHub.

good looks like: a stranger with the stated environment could start from nothing and reach the trigger: every command, input file content, and setting needed is in the report (commands, or click-by-click steps where the issue is not a CLI one). 

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->
Used by: behavior-matches

where:
- Candidate repro report: the output excerpts, logs, screenshots, and
  any control run.
- Read them against: the error text, exit code, crash, or wrong output
  the Issue describes as the bug.
- Thread highlights: a maintainer's description of the exact symptom.

under live mode: the output pasted in my draft, read against the issue body on GitHub and my own terminal output.

good looks like: the artifact itself shows the same symptom the issue
describes: the same error message, exit code, or wrong value. A
different error that merely also looks like failure (a syntax error, an
argument-validation message, a compile error, a normal run) is an
adjacent behavior and fails, however confident the narration around it.
A control run that changes only the trigger and makes the symptom go
away is strong support. For a cannot-reproduce, the artifact shows the
real attempt: the commands run and the output that came back.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->
Used by: behavior-matches, claim-specific

where:
- The claim sentences in the Candidate repro report and Candidate claim
  comment ("I reproduced", "confirmed", "the root cause is", "guaranteed").
- Read them against: the artifacts shown in the same report.

under live mode: the claim sentences in my draft, read against the
output I actually pasted.

good looks like: every claim is backed by an artifact on the page. "I
reproduced X" needs output that shows X; "the cause is Y" needs shown
evidence of Y, otherwise it must be worded as a hypothesis. An honest
cannot-reproduce passes: it says what was tried, shows the output, names
how the environment differed from the issue's, and what a triggering
setup probably needs. Fails: certainty with no artifact, or an
"expected vs actual" that contradicts the artifact shown.

## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->
Used by: claim-specific, policy-disclosure, fix-plan

where:
- Candidate claim comment, read against the Issue (its files, functions,
  symptom).
- Repo facts: contribution policy (its AI policy) and bug-report
  template, read against both the claim comment and the repro report.
- Thread highlights: anything a maintainer asked contributors to do.

under live mode: my draft comment, read against the issue on GitHub and
the repo's CONTRIBUTING.md (and any AI policy file it links).

good looks like:
- Claim comment: names something specific to this issue (the symptom,
  file, function, or version) and states the next step as investigation
  or reproduction. A comment that could be pasted on any issue ("+1",
  "assign me please") fails; promising a fix or a date fails.
- AI disclosure: only when the policy explicitly requires disclosing AI
  use, the claim comment or report must say an AI tool was used and how
  (e.g. "I used an AI assistant to organize this report; I ran every
  step myself"). Missing that disclosure is a fail, however good the
  repro. Treat every package as AI-assisted work. A policy that only
  allows AI, or asks that comments be in the author's own words, does
  not require a disclosure line; pass if the comment reads as the
  author's own words. No AI policy at all: pass.