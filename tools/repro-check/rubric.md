# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | The versions of every environment package used in the reproduction | These environments are listed; if they differ from the version or platform the issue targets, the report explicitly calls out the difference | required |
| claim-specific | The comment's content | Fail if the comment is vague and says nothing of substance; fail if it guarantees a fix by a certain date without strong grounds. The comment should mention specifics of the issue and state the next step | required |
| steps-followable | The command lines used in the reproduction that can be run directly | Complete command lines are given that anyone can run, and they match what the issue requires | required |
| behavior-matches | Dev-tool screenshots, code blocks, etc. | The evidence clearly shows behavior consistent with what the issue describes. If the bug was not reproduced, it still passes as long as the evidence shows a real attempt and explains how the environment differs from the issue's | required |
| fix-plan | Text describing current testing progress and how a fix is planned | The reasoning is sufficient and complete | preferred |
| policy-disclosure | The contribution policy in the repo facts, especially the AI policy, and any requirements stated in the issue | If the repo or issue has such a requirement, the comment or report must respond to each one; if the repo and issue have no such requirement, pass | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

accept if every required check passes, otherwise reject;
preferred checks never change the verdict;
An unclear grade on a required check counts as fail
