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

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

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

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

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

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
