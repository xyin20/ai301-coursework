# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72

**Verdict output**

Active project — pass: the repository is not archived, and its five latest main-branch commits include three dated 2026-09-16.

Contribution policy — pass: `docs/CONTRIBUTING.md` describes the course contribution workflow and contains no restriction against AI-assisted work.

Bounded change — pass: the issue identifies one failure mode, the expected fail-closed behavior, two relevant files, and a covering xfail test to enable.

Available to claim — pass: GitHub shows no assignee, relationship, branch, pull request, or work-in-progress comment. The Path Review house rule would also ignore classmates' claim comments.

Maintainer path — pass: the issue author, Andrew Burke, authored all three main-branch commits dated 2026-09-16 and supplied the relevant files, expected behavior, and estimated effort.

Fit summary: accept. This is the strongest fit because it is a 1–2 hour Python bug fix with an existing regression test and a clear security behavior.

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
  "checks": [
    {
      "name": "Active project",
      "grade": "pass",
      "evidence": "The repository is not archived, and three of its five latest main-branch commits are dated 2026-09-16."
    },
    {
      "name": "Contribution policy",
      "grade": "pass",
      "evidence": "docs/CONTRIBUTING.md defines the course workflow and states no restriction against AI-assisted contributions."
    },
    {
      "name": "Bounded change",
      "grade": "pass",
      "evidence": "Issue #72 specifies malformed hashes, return False as the expected behavior, core/security.py and tests/unit/test_security.py, and removal of one xfail marker."
    },
    {
      "name": "Available to claim",
      "grade": "pass",
      "evidence": "The issue has no assignee, relationship, development branch, pull request, or work-in-progress comment."
    },
    {
      "name": "Maintainer path",
      "grade": "pass",
      "evidence": "Issue author Andrew Burke also authored the repository's three latest commits and provided concrete implementation and test guidance."
    }
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

**Run history**

1. `agreement: 20/20 scored items  (bar: 18/20: PASS)`

This was the only completed run. Codex executed the rubric directly because the saved Claude OAuth session was expired; `eval-run.txt` records that substitution rather than claiming to be a Sonnet harness run.

**Issue analysis**

`issue-12` — my rubric decided `reject`; the gold label was `reject`. The bundle's policy says, `We do not accept AI-generated code or documentation.` The project was active, the issue was bounded, and nobody held a current claim, but that explicit prohibition failed the required Contribution policy check and therefore forced rejection.

**Check rationale**

Contribution policy: `Pass when the repository permits the planned contribution workflow or states no policy. Fail when the policy prohibits AI-generated code or documentation, or otherwise makes this course's AI-assisted contribution workflow ineligible. A policy that permits assistive AI with human review passes.`

I kept the distinction between a ban and a human-review requirement because this course uses AI assistance but still expects the student to understand, test, and own every change. The check rejects a genuinely incompatible repository without excluding projects that allow responsible assistive use.

**Trade-offs**

This check rejects `issue-12` even though it passes the liveness, scope, and availability checks. I accept that trade-off because choosing an otherwise excellent issue is still a poor decision when the required course workflow conflicts with the repository's explicit contribution policy.

---

## Selection rationale

**Selection rationale**

1. Issue #72 fits my Python experience and the available time. It is estimated at 1–2 hours, names the implementation and test files, and already has an xfail regression test that defines completion.
2. The verdict correctly identified an active project, a permitted workflow, a bounded change, and no blocking claim. Beyond the rubric, I weighed the usefulness of learning a fail-closed security pattern and the low setup risk of a focused unit-tested change.
3. Claiming should be straightforward. The issue currently has no assignee or pull request, and Path Review explicitly allows classmates to work on the same issue. The harder part will be confirming the exact passlib exception boundary and preserving `False` for every malformed stored-hash case without masking unrelated errors.

---

Related paths: `eval-run.txt` in this directory; the skill files in `tools/issue-select/`.
