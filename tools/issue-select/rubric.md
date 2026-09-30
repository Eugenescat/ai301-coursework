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
| maintainer-responsive | repo-facts block: the maintainer response sample, compared against the capture date stamped at the top of the bundle | If the issue is opened by a maintainer or contributor, pass. If the issue is opened within 3 days before the capture date, pass. Otherwise at least one response authored by a maintainer or repo member within 90 days before the capture date. | required |
| repo-active | repo-facts block: commit activity and release recency, plus any archived or deprecated marker | At least one default-branch commit within 90 days before the capture date, and no archived or deprecated marker | required |
| unclaimed | repo-facts block: assignee field and linked-PR state; plus the comment thread | No assignee listed, no open linked PR against this issue, and no comment claiming the work within 90 days before the capture date | required |
| policy-permits | repo-facts block: the repo's stated contribution policy lines | The policy does not bar an unsolicited outside contribution: it does not restrict PRs to maintainers or a mentorship program, does not require the issue be assigned before work starts, and states no blocking precondition the bundle shows unmet. The policy doesn't bar AI-generated contributions | required |
| scope-bounded | Issue body and comment thread | The issue names a specific reproducible failure or change requirement, and the thread shows no unresolved disagreement about what the fix should be | required |
| maintainer-endorsed | repo-facts block: labels and who applied them; comment thread | A maintainer applied a good-first-issue, help-wanted, or bug label, or replied confirming the issue is valid | preferred |

## Verdict rule

accept if every required check passes; reject if any required check is graded fail or unclear. unclear counts as fail. preferred checks never change the verdict; they rank the accepted issues.

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->
