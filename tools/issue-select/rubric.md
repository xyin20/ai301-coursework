# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Active project | The repo-facts block: archived status, latest release date, last push date, and the last 5 default-branch commit dates. | Pass when the repository is not archived and at least one default-branch commit, release, or branch push is dated within 12 months of the bundle's capture date. A recent issue report by itself is not activity. | required |
| Contribution policy | The contribution-policy line in repo facts and any linked policy text included in the bundle. | Pass when the repository permits the planned contribution workflow or states no policy. Fail when the policy prohibits AI-generated code or documentation, or otherwise makes this course's AI-assisted contribution workflow ineligible. A policy that permits assistive AI with human review passes. | required |
| Bounded change | The issue title and body, plus maintainer comments that clarify the requested result. | Pass when the evidence identifies one deliverable with a concrete expected behavior, named files or components, or a short finite list of changes that a newcomer could verify. Fail for umbrella/mega/tracking issues, codebase-wide cleanup, an unresolved product or design decision, or a request whose key asset or expected behavior is still TBD. A short report may pass when a maintainer filed it and names the specific faulty behavior or finite fixes. | required |
| Available to claim | The repo-facts assignees and linked-PR fields, then the comment thread for explicit work/claim statements and maintainer release or reassignment. | Pass when there is no current assignee, no open linked or explicitly referenced implementation PR, and no still-current statement that someone is working on it. Ignore closed/merged PRs and claims that a later maintainer or bot explicitly released, unassigned, or invited others to take. Treat an old claim with no open PR as stale after 30 days unless later comments show work is continuing. | required |
| Maintainer path | The issue author association, maintainer comments on the issue, and the maintainer first-response sample in repo facts. | Pass when a maintainer authored or clarified the issue, or at least one sampled issue received an owner/member/collaborator response within 30 days. Otherwise grade unclear. | preferred |

## Verdict rule

Accept only when every required check passes. Reject when any required check fails or is unclear. Preferred checks never change accept/reject; they only rank accepted issues, with a passing Maintainer path ranked ahead of an unclear one.
