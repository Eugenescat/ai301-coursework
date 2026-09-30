# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

[https://github.com/codepath/pathreview-ai301-fa26-s1/issues/26]

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
I graded both. Both are accepted, and I'd rank #26 first. Every required check passes on each, and both have the preferred maintainer-endorsed signal.

1. #26: Add a safety event count to the health check endpoint (accept)
- Why it fits you best: it's a small, precisely described Python/FastAPI bug. The issue names the broken line: /health hard-codes safety_events_last_hour as 0. It also names the method that fixes it: SafetyMonitor.get_event_count() in safety/monitoring.py. You'd touch two files, estimated at 2–4 hours, and the tier-1, good-first-issue and bug labels were applied by the maintainer.
- That makes it a gentle first look at how a FastAPI route calls into a service layer, without the "too complicated" risk.
- HungH206 commented "I would like to claim this issue for Unit 2" on 2026-09-23. That's a classmate's claim, so the house rule says to ignore it.

2. #36: POST /reviews has no test for a profile with no ingested documents (accept)
- It's also a good fit on paper: FastAPI TestClient, pytest, tier-1, good first issue, 2–3 hours.
- It ranks lower because the issue's premise doesn't hold. Kunalkrk's reproduction (2026-09-30) shows the endpoint returns 200 and creates a pending review for an empty profile. It doesn't return an error, so there's nothing yet for the requested test to check.
- Doing it properly probably means adding validation to create_review, likely returning a 422, and nobody has decided that yet. It's an open question rather than a disagreement, so it passes scope-bounded as your rubric is written. In practice, though, the work is bigger and fuzzier than the issue says.

Compared with #51 from earlier: both of these beat it on your "avoid too complicated" preference. #51 is tier-3, estimated at 5–7 hours, and has no newcomer label.

Possible rubric change: your scope-bounded check can't spot a stale premise like #36's. If you want it to, add something like "no thread comment shows the described behavior doesn't occur as stated".

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/26",
    "checks": [
      {"name": "maintainer-responsive", "grade": "pass", "evidence": "Issue opened 2026-09-10 by Aburke225 (author_association: COLLABORATOR)"},
      {"name": "repo-active", "grade": "pass", "evidence": "Last default-branch commit 2026-09-16 (14 days before 2026-09-30); archived: false"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees: []; no linked or mentioning PR among #74-#79; HungH206's 2026-09-23 claim is a classmate's and ignored under the Path Review house rule"},
      {"name": "policy-permits", "grade": "pass", "evidence": "docs/CONTRIBUTING.md asks only to comment before working; no assignment requirement, no AI restriction"},
      {"name": "scope-bounded", "grade": "pass", "evidence": "Body: /health reports safety_events_last_hour as literal 0; fill it from SafetyMonitor.get_event_count(); no disagreement in thread"},
      {"name": "maintainer-endorsed", "grade": "pass", "evidence": "Aburke225 applied 'bug' and 'good first issue' labels on 2026-09-10"}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/36",
    "checks": [
      {"name": "maintainer-responsive", "grade": "pass", "evidence": "Issue opened 2026-09-10 by Aburke225 (author_association: COLLABORATOR)"},
      {"name": "repo-active", "grade": "pass", "evidence": "Last default-branch commit 2026-09-16 (14 days before 2026-09-30); archived: false"},
      {"name": "unclaimed", "grade": "pass", "evidence": "assignees: []; no linked or mentioning PR among #74-#79; Kunalkrk's 2026-09-30 claim is a classmate's and ignored under the Path Review house rule"},
      {"name": "policy-permits", "grade": "pass", "evidence": "docs/CONTRIBUTING.md asks only to comment before working; no assignment requirement, no AI restriction"},
      {"name": "scope-bounded", "grade": "pass", "evidence": "Body: add a test in tests/unit/test_review_routes.py that POST /reviews with no ingested content returns an error; thread has one commenter, no disagreement"},
      {"name": "maintainer-endorsed", "grade": "pass", "evidence": "Aburke225 applied 'good first issue' label on 2026-09-10"}
    ],
    "verdict": "accept"
  }
]
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

13/20
18/20
20/20

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

**issue-12** (bookwyrm-social/bookwyrm#1133)

- My rubric's first decision (13/20 run): **accept**
- Gold label: **reject**
- My rubric's final decision (20/20 run, eval-run.txt): **reject**

The bundle's contribution-policy line says: "We do not accept AI-generated code or documentation." Gold rejects it because "passes every liveness, scope, and claim check; the repo's contributing docs ban AI-generated code and documentation outright."

My original `policy-permits` pass condition was: "The policy does not bar an unsolicited outside contribution: it does not restrict PRs to maintainers or a mentorship program, does not require the issue be assigned before work starts, and states no blocking precondition the bundle shows unmet." The grader's evidence was: "Stated policy only bars AI-generated contributions; no restriction to maintainers/mentorship program or pre-assignment requirement." So the grader did see the AI ban, but my condition only listed three kinds of barriers and an AI ban was not one of them, so it graded the check pass by the letter of my rule. Every other check also passed, so the issue was accepted.

Since I use AI tools to contribute, an AI ban is a real blocker for me. I added "The policy doesn't bar AI-generated contributions" to the pass condition, and in the final run issue-12 is rejected, matching gold. This was also the only issue in the policy category, so missing it failed the category floor.


**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

"If the issue is opened by a maintainer or contributor, pass. If the issue is opened within 3 days before the capture date, pass. Otherwise at least one response authored by a maintainer or repo member within 90 days before the capture date."

The original rule only considered the responses of the maintainers in the samples. In sample of issue-06, 4 of the entries were made by the maintainers themselves on the same day. In issue-14, only 1 was made the day before. Both were judged as fail, but gold was accepted. I added two exceptions (made by the maintainers or contributors; made within 3 days), and the problems were corrected in these two cases.

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

The scope of "contributor" is quite broad. Anyone who has merged a pull request on GitHub is considered a contributor. Therefore, this check can be easily bypassed and will not be able to prevent the maintenance of repos that have become inactive. This didn't bar dead-repo type issues, inlcuding 02、07、17. They are rejected by repo-active check.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

1. **Fit and time.** This issue is in Python and touches a FastAPI route (`api/routes/health.py`) and the safety layer (`safety/monitoring.py`), so it fits my Python background and my goal of getting familiar with a dev framework. It is small: the body names the two files, says exactly what is wrong (`safety_events_last_hour` is hard-coded to `0`), and names the method that can fill it (`SafetyMonitor.get_event_count()`). The estimate is 2–4 hours, which fits the time I have this unit.

2. **What the verdict got right, and what I weighed myself.** The skill correctly found that the issue is maintainer-filed and labeled `bug` and `good first issue`, the repo is active, nothing is assigned or linked to a PR, and the scope is one bounded change. What my rubric cannot see is size: none of my checks measures effort. I first picked #51, which also passed, but it is tier-3 with a 5–7 hour estimate and a migration/model mismatch already on main, which conflicts with my "avoid too complicated issues" goal. So I switched to #26, a tier-1 issue, by my own judgment.

3. **Difficulty in claiming it.** I need to check how `get_event_count()` returns per-type counts and decide how to turn them into a single "last hour" number, which the issue does not spell out.


---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
