# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72

**Live-mode verdict (verbatim, `issue-select` skill, live mode)**

## Summary

**Issue:** [#72](https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72) — `verify_password` raises `UnknownHashError` on malformed stored hashes instead of returning False

| Check | Grade | Evidence |
|---|---|---|
| Active project | pass | Repo not archived; last default-branch push 2026-09-16, commits as recent as that date — well within 12 months. |
| Contribution policy | pass | `docs/CONTRIBUTING.md` states the standard PR workflow with no AI-restriction language; repo's own recent commits carry `Co-Authored-By: Claude Opus 5`, showing AI-assisted contributions are already accepted here. |
| Bounded change | pass | Issue names the exact defect (`UnknownHashError` should fail closed, return `False`), the two files to touch (`core/security.py`, `tests/unit/test_security.py`), and the specific xfail marker (`H-05`) to remove — one deliverable, concretely verifiable. |
| Available to claim | pass | `assignees: []`, `closedByPullRequestsReferences: []`, zero comments on the issue — no claim, no open PR. |
| Maintainer path (preferred) | pass | Author `Aburke225` has `author_association: COLLABORATOR` on the repo, so the issue is maintainer-authored. |

All required checks pass, so the issue is accepted. It also fits the stated profile well: a small, self-contained Python bug fix with a named test to update — exactly the "bounded bug fix with reproducible verification" the profile asks for, with no domain-specific ML/RAG knowledge required.

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
  "checks": [
    {"name": "Active project", "grade": "pass", "evidence": "Repo not archived; last default-branch push 2026-09-16T21:50:20Z, within 12 months."},
    {"name": "Contribution policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md states no AI-restriction; recent repo commits themselves carry 'Co-Authored-By: Claude Opus 5', so AI-assisted work is already accepted."},
    {"name": "Bounded change", "grade": "pass", "evidence": "Issue names the exact bug (UnknownHashError should fail closed to False), two specific files (core/security.py, tests/unit/test_security.py), and the xfail marker (H-05) to remove."},
    {"name": "Available to claim", "grade": "pass", "evidence": "assignees: [], closedByPullRequestsReferences: [], comments: [] — no assignee, no linked PR, no claim comment."},
    {"name": "Maintainer path", "grade": "pass", "evidence": "author_association: COLLABORATOR for issue author Aburke225 — issue is maintainer-authored."}
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

**Run history**

1. `agreement: 16/20 scored items  (bar: 18/20: below the bar)` — categories: claimed 4/4, clear-accept 5/8, dead-repo 3/3, policy 1/1, scope 3/4. Disagreements: issue-01, issue-04, and issue-19 (all gold `accept`) were wrongly rejected on Bounded change; issue-15 (gold `reject`) was wrongly accepted on the same check.
2. Revised the Bounded change check's pass condition in `rubric.md`: explicitly allow a finite list of named files/pages (a documentation issue) and a bug report that also lists optional follow-on enhancements or more than one candidate approach, as long as the core fix is identifiable; explicitly fail a thread showing a history of repeated abandoned attempts (multiple closed, unmerged linked PRs, or contributors repeatedly claiming and going inactive).
3. `agreement: 19/20 scored items  (bar: 18/20: PASS)` — categories: claimed 4/4, clear-accept 7/8, dead-repo 3/3, policy 1/1, scope 4/4. This is the final run, saved as `eval-run.txt` in this directory.

**Issue analysis**

`issue-15` (zulip/zulip#19589) — my rubric decided `reject`; the gold label was `reject`. The ask itself reads bounded on its face (split a Slack-style outgoing-webhook payload into separate `command` and `text` fields), and the pre-revision rubric graded only that surface text and passed it. But the bundle shows 97 comments spanning 2021–2024 and two previously closed, unmerged linked PRs (`#20840`, `#23123`) — a repeated cycle of contributors claiming the issue and going inactive without landing a fix. That history is exactly what the revised Bounded change clause is written to catch: a request that looks concise in isolation but has already defeated multiple attempts is telling you something about its real difficulty that the issue body alone won't show.

**Check rationale**

`"a thread showing a history of repeated abandoned attempts (multiple closed, unmerged linked PRs, or several contributors claiming and then going inactive) — that history is evidence the issue is harder than it reads, even when the current ask looks concise."`

I added this clause because the pre-revision rubric only ever looked at what the issue *said*, never at what had already happened to it. A newcomer can't verify "is this really as small as it sounds" from the issue text alone on a repo with years of comment history, but the eval bundle hands you that history for free, so the check should use it. I kept the bar at "multiple" abandoned attempts rather than any single stale claim, so a normal issue that sat untouched for a while (which the Available-to-claim check already treats leniently after 30 days) doesn't get penalized twice for the same thing.

**Trade-offs**

The revision still leaves one disagreement: issue-04 (zxlive#555, "Missing several basic rule previews") is gold `accept` but my rubric still grades `reject` on Bounded change. The issue names the missing behaviors but ends the list with "etc.", which a literal read of "the core fix itself is identifiable" can still treat as open-ended, even though the maintainer clearly means a small, enumerable set of preview rules. I accepted that trade-off rather than loosening the check further, because the failure mode it produces — occasionally rejecting a genuinely bounded issue that happens to trail off with "etc." — is a safer mistake for a first-time contributor to make than the alternative: loosening the wording enough that a real open-ended list slips through as bounded. A false reject costs one candidate out of twenty; a false accept sends a newcomer into a scope trap on their first contribution.

---

## Selection rationale

1. Issue #72 lines up with what I'm actually equipped for right now. It's a small Python security bug — `verify_password` should fail closed and return `False` on a malformed stored hash instead of raising `UnknownHashError` — and the issue already names the two files I'd touch (`core/security.py`, `tests/unit/test_security.py`) and the exact xfail marker (`H-05`) that defines when I'm done. That's about as close to a guided first PR as this repo offers.

2. The live verdict came back `accept` on every required check, and a couple of those results told me more than a plain pass/fail would. The contribution-policy check didn't just find silence in `CONTRIBUTING.md` — it found actual recent commits in the repo carrying a `Co-Authored-By: Claude Opus 5` trailer, meaning AI-assisted contributions aren't just tolerated on paper, they're already merged into this project. And the maintainer-path check landed on pass because the issue author is a COLLABORATOR, not just a random reporter, so I'm not waiting on someone else to confirm this is a real, wanted fix. Between the rubric's answer and those two extra data points, I felt more confident in this pick than the bare `accept` verdict alone would have given me.

3. Claiming it should be low-friction — no assignee, no linked PR, and zero comments on the issue, so nobody's already staked a claim (and Path Review's house rule means it wouldn't matter much even if they had). The part I expect to actually be hard is scoping the fix correctly: passlib's hashing functions can raise more than one kind of exception for a malformed hash, and I need to make sure I catch the right one(s) to return `False` without accidentally swallowing an unrelated bug. Getting that boundary right, and making sure the `H-05` xfail test still exercises a real malformed-hash case rather than a trivial one, is where the actual work is.

---

Related paths: `eval-run.txt` in this directory; the skill files in `tools/issue-select/`.
