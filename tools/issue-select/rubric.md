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
| maintainer_active | Comment thread; repo-facts block: last 5 default branch commit dates, latest release date, maintainer first-response sample | At least one maintainer action within 60 days of the capture date. A maintainer comment, a default branch commit, a merged PR, or a published release all count, since merging and releasing require maintainer access even when the author's association is not shown | required |
| repo_in_use | Repo-facts block: last 5 default branch commit dates, archived flag; README top section | Newest default branch commit is within 90 days of the capture date, repo is not archived, and the README has no deprecation or "no longer maintained" notice | required |
| issue_open_and_wanted | Issue state and labels; maintainer comments in the thread | Issue is open, has none of the labels wontfix, invalid, blocked, or needs design, and is not marked as a duplicate of another issue. A label marking this issue as the primary or canonical issue that others duplicate (such as duplicate::primary) does not count as a duplicate. No maintainer comment declines or postpones the change | required |
| not_claimed | Assignees field; linked or referencing PRs; comment thread | No assignee, no open PR that references the issue, and no claim comment ("I'll take this", "working on it") from another person posted within 30 days of the capture date. A claim older than 30 days with no follow up counts as stale and passes | required |
| scope_fits_newcomer | Issue body, labels, maintainer comments, and comment count | Pass unless the issue shows positive evidence of oversized, undefined, or deceptively hard scope. Fail only if at least one holds: (a) the issue or a maintainer asks for a redesign, rewrite, refactor, or migration of code across multiple modules, or calls the work large, an epic, or needing an RFC or design doc; (b) a question or required input that the issue or a maintainer says must be settled before work starts is still open, including anything marked TBD or undecided; (c) the issue states no observable problem or goal, meaning no behavior, error, output, or requested feature a contributor could check a fix against; (d) it asks for a new feature, tool, or element type that spans more than one package or subsystem and no maintainer has approved it in the thread; (e) the thread has more than 50 comments, or 3 or more earlier contributors claimed or started it without a merged fix. Not naming files, listing examples with "etc.", and a reporter's guesses about causes or possible approaches are not reasons to fail. Items marked optional, lower priority, or "consider" are not open decisions. Writing, moving, or reorganizing documentation across pages is never a redesign, migration, or new feature under (a) or (d), however many pages it touches | required |
| no_special_access | Issue body and comments | Doing the work needs no credentials, paid service, special hardware, or private or production data | required |
| tests_nearby | Repo-facts block or locations in references/evidence-guide.md | A test file exists for the module the issue touches. Documentation only changes pass | preferred |
| policy_allows_contribution | Repo-facts block: contribution policy line (CONTRIBUTING.md or linked contributing docs), especially any Generative AI section | The policy does not prohibit AI generated or AI assisted code or documentation, and does not require anything a course contributor cannot do before opening a PR (such as prior maintainer approval of the contributor, or signing an agreement the contributor cannot sign). Policies that welcome AI tools or only require the contributor to review and understand AI output pass. If no policy is stated, pass | required |




## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

"Accept only if every required check passes. Preferred checks never change the verdict; they only rank accepted issues. A required check graded unclear counts as fail. All time windows are measured from the repo-facts capture date in eval mode, and from today in live mode."