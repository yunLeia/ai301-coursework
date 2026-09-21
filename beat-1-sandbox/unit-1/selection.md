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

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72


**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** 

````
⏺ Both candidates are in the scoped repo (codepath/pathreview-ai301-fa26-s3). Graded each
  independently against rubric.md; the Path Review house rule applies (classmates' claims don't
  block).

  Ranked read-out

  1. #72 — verify_password raises UnknownHashError — accept. Best fit: it's Python backend logic
  in core/security.py with a paired @pytest.mark.xfail(strict=True) test at
  tests/unit/test_security.py:218 you flip green — exactly the "read unfamiliar code, work with
  tests, ship a clean PR" practice you want, and squarely backend rather than docs.

  - maintainer_active: pass — Aburke225 pushed to main 2026-09-16, 5 days ago
  - repo_in_use: pass — newest main commit 2026-09-16, isArchived: false, no deprecation notice
    in README
  - issue_open_and_wanted: pass — OPEN; labels bug, good first issue, api, tier-1; no
    wontfix/invalid/blocked/needs-design, no duplicate marker
  - not_claimed: pass — no assignees, no open PRs in the repo at all; two referenced events
    (rafiatasafi, xyin20, 2026-09-20) are commits in their own coursework forks, not open PRs or
    claim comments — and the house rule ignores classmate claims regardless
  - scope_fits_newcomer: pass — observable goal ("return False, not raise"), two named files,
    zero comments, no redesign/open-decision language
  - no_special_access: pass — pure library behavior; no credentials or data needed
  - tests_nearby: pass (preferred) — tests/unit/test_security.py exists and already covers the
    bug
  - policy_allows_contribution: pass — docs/CONTRIBUTING.md has no AI restriction; the "first PR
    may need a maintainer to start CI" note is a post-submission step, not pre-approval

  2. #73 — README and .env.example disagree about the LLM key — accept. Genuine and verified
  (.env.example:18-19 lists only LLM_PROVIDER=mock and OPENAI_API_KEY, while README says add
  OPENROUTER_API_KEY), but it's a docs/config edit, so it does less for the backend and testing
  practice you named.

  - maintainer_active / repo_in_use / policy_allows_contribution: pass — same repo-level
    evidence as above
  - issue_open_and_wanted: pass — OPEN; labels bug, good first issue, docs, tier-1; no blocking
    labels
  - not_claimed: pass — no assignees, no comments, no referencing PRs
  - scope_fits_newcomer: pass — two files, one observable contradiction; docs reorganization is
    never a redesign under (a)/(d)
  - no_special_access: pass — no key is actually needed to make the files agree
  - tests_nearby: pass (preferred) — documentation-only change

```json
  [
    {
      "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
      "checks": [
        {"name": "maintainer_active", "grade": "pass", "evidence": "Maintainer Aburke225 
  committed to default branch main on 2026-09-16, 5 days before today (2026-09-21)"},
        {"name": "repo_in_use", "grade": "pass", "evidence": "Newest main commit 2026-09-16 (5 
  days), isArchived: false, README has no deprecation notice"},
        {"name": "issue_open_and_wanted", "grade": "pass", "evidence": "state OPEN, labels bug /
  good first issue / api / tier-1; no wontfix, invalid, blocked, needs design, or duplicate 
  marker"},
        {"name": "not_claimed", "grade": "pass", "evidence": "assignees: []; `gh pr list --state
  all` returns no PRs in the repo; the two 2026-09-20 referenced events are commits in 
  rafiatasafi's and xyin20's own coursework repos, not open PRs or claim comments"},
        {"name": "scope_fits_newcomer", "grade": "pass", "evidence": "Observable goal ('should 
  fail closed (return False), not raise'), two named files, zero comments, no redesign/epic/TBD 
  language"},
        {"name": "no_special_access", "grade": "pass", "evidence": "Issue is passlib 
  UnknownHashError handling in core/security.py; no credentials, paid service, or private data 
  mentioned"},
        {"name": "tests_nearby", "grade": "pass", "evidence": "tests/unit/test_security.py:218 
  holds the covering @pytest.mark.xfail(strict=True) test referencing issue #72 (manifest 
  H-05)"},
        {"name": "policy_allows_contribution", "grade": "pass", "evidence":
  "docs/CONTRIBUTING.md states no AI restriction; its only gate is a maintainer releasing CI 
  after the PR is opened"}
      ],
      "verdict": "accept"
    },
    {
      "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
      "checks": [
        {"name": "maintainer_active", "grade": "pass", "evidence": "Maintainer Aburke225 
  committed to default branch main on 2026-09-16 and labeled this issue the same day"},
        {"name": "repo_in_use", "grade": "pass", "evidence": "Newest main commit 2026-09-16 (5 
  days), isArchived: false, README has no deprecation notice"},
        {"name": "issue_open_and_wanted", "grade": "pass", "evidence": "state OPEN, labels bug /
  good first issue / docs / tier-1; no blocking labels and no maintainer comment declining 
  it"},
        {"name": "not_claimed", "grade": "pass", "evidence": "assignees: [], comments: [], no 
  linked or referencing PRs in the issue timeline"},
        {"name": "scope_fits_newcomer", "grade": "pass", "evidence": "Verified contradiction: 
  .env.example lines 18-19 give LLM_PROVIDER=mock and OPENAI_API_KEY while README says 'add your
  OPENROUTER_API_KEY to .env'; two named files, no open decisions"},
        {"name": "no_special_access", "grade": "pass", "evidence": "Work is editing README.md 
  and .env.example; no actual API key or private data required"},
        {"name": "tests_nearby", "grade": "pass", "evidence": "Documentation/config-only change,
  which the rubric passes by default"},
        {"name": "policy_allows_contribution", "grade": "pass", "evidence":
  "docs/CONTRIBUTING.md contains no prohibition on AI-generated or AI-assisted work"}
      ],
      "verdict": "accept"
    }
  ]
```
````

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.


**Run history**

1. `--limit 3`, first rubric: 2/3 (issue-01 rejected on `scope_fits_newcomer`)
2. `--limit 3`, loosened the file count wording: 2/3
3. `--limit 3`, new scope row accidentally added next to the old one: 2/3
4. `--only issue-01 --out`, to read the grader's reasoning: 0/1
5. `--only issue-01`, fixed a merged table row, added `issue_open_and_wanted`, defined what an open design decision is: 1/1
6. Full run: 16/20 (clear-accept 4/8, every other category perfect)
7. `--only` on 11 issues (the 4 misses plus every scope and dead repo issue), scope rewritten to fail only on positive evidence, commits and releases counted for `maintainer_active`: 8/11
8. Full run: 18/20, category floor unmet (policy 0/1)
9. `--only issue-01,issue-12`, added `policy_allows_contribution` and limited scope clause (a) to code: 2/2
10. Full run, saved as `eval-run.txt`: 19/20, bar PASS

**Issue analysis**

issue-19. My rubric decided **reject**, failing `scope_fits_newcomer`. The gold label is **accept**.

The grader's evidence in my final run:

> "Issue names two unresolved root causes ('There are two potential causes which should be fixed') plus three further suggestions (multiprocessing, category-scoped matching, separate thread for rewrite application) spanning matcher engine, UI update path, and threading model with no settled approach"

My scope check says "a reporter's guesses about causes or possible approaches are not reasons to fail," but it also fails an issue on (a) a redesign across modules or (b) an open question that must be settled before work starts. The reporter wrote that the causes "should be fixed," so the grader read the guesses as requirements, and three suggestions spanning several subsystems looked like an unsettled redesign. The two parts of my rule pull against each other on this wording. The same issue was accepted in runs 7 and 8 with no change that affected it, so this is a borderline call where the grader flips, not a clear miss. I left it because I was already at 19/20, and tightening the carve out risked letting issue-15 and issue-20 back through.

**Check rationale**

> | policy_allows_contribution | Repo-facts block: contribution policy line (CONTRIBUTING.md or linked contributing docs), especially any Generative AI section | The policy does not prohibit AI generated or AI assisted code or documentation, and does not require anything a course contributor cannot do before opening a PR (such as prior maintainer approval of the contributor, or signing an agreement the contributor cannot sign). Policies that welcome AI tools or only require the contributor to review and understand AI output pass. If no policy is stated, pass | required |

My first rubric had no check that read the contribution policy. Issue-12 was rejected in run 6 only by accident, because the old strict scope check caught it. Once I loosened scope in run 8, issue-12 was accepted and the policy category dropped to 0/1, failing the category floor. Its bundle quotes BookWyrm's policy: "We do not accept AI-generated code or documentation." This course has me work with Claude Code, so a repo with that policy is off limits no matter how good the issue is. I added the sentence letting through policies that only require reviewing AI output because conda's policy (issue-01) says contributors "must review and understand AI-generated content," and I did not want the grader to read that as a restriction.

**Trade-offs**

This check rejects any repo whose policy bans AI generated contributions, even when the issue itself is ideal, and a strict grader could read a vaguely worded policy as a ban. To test that it did not overreach, I used a canary: in run 9 I reran `--only issue-01,issue-12`. Issue-12 flipped to reject as intended, and issue-01, whose policy welcomes AI tools but requires reviewing the output, stayed accept. In the final full run, every other category kept its result (claimed 4/4, dead repo 3/3, scope 4/4), so the check did not change anything outside policy.

---

## Selection rationale

**Selection rationale**

1. [Fit and time: why #72 matches your interests and how the 1 to 2 hour estimate fits your schedule.]
2. [What the verdict got right, and what you weighed that the rubric could not.]
3. [Difficulty in claiming it.]

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
