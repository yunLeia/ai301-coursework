# Evidence guide: where proof lives in a reproduction package

The map for every check in `rubric.md`. In eval mode the bundle is the
whole world: quote from it, fetch nothing. In live mode the drafts are
the candidate side and the issue side is gathered from GitHub.

A rule for every family: read the issue first and write down, in one
line, the exact trigger and the exact symptom it reports. Every later
judgment is a comparison against that line.

## Environment

Where it lives:
- Eval: the repro report's environment line or block (often labeled
  Environment, sometimes a first line like "fd 10.4.2, Arch Linux").
  The issue's target lives in the Issue section (versions, OS, build
  the reporter names) and in the Thread highlights (a maintainer saying
  "confirmed on main" or "only on Windows").
- Live: the student's repro draft; the issue body and its comments on
  GitHub; the repo's setup docs (for Path Review, `docs/SETUP.md` and
  `pyproject.toml` for the Python and library versions).

What good looks like: the software version and the platform are named,
plus any variable the issue or thread ties the bug to (OS, driver,
backend, build profile, shell, runtime or library version). If the run
used a different version or platform than the issue targets, the report
says so in plain words. A missing record, or a missing variable the
issue itself flags as mattering, is not good enough however good the
rest looks.

## Steps

Where it lives:
- Eval: the numbered steps or command block in the repro report, plus
  any config or input file content it quotes.
- Live: the student's repro draft only. Files in the student's working
  directory that the draft does not quote do not count: the stranger on
  the thread cannot see them.

What good looks like: starting state (fresh clone, clean directory,
named commit or release) through to the exact command or call that
fires the bug, with every input shown or quoted. A stranger with the
public repo and nothing else could type it in. A small input file may
be described instead of pasted when the description leaves nothing to
guess (which sections, which keys, which values matter). Red flags: a private
repository or unshared config, "set up the project" with no commands,
a step that is described but never shown, a step that skips the
trigger.

## Behavior shown

Where it lives:
- Eval: output excerpts, log lines, tracebacks, exit codes, printed
  values, and descriptions of observed screens in the repro report,
  including any control run.
- Live: the same inside the student's repro draft.

What good looks like: an artifact that shows the issue's own symptom,
read literally. Compare error type and message, exit code, crash vs
graceful error, and the specific wrong value against the one line
symptom from the issue. A different error (a syntax error, an unbound
variable, an argument validation message) is an adjacent behavior, not
the bug, even when the report calls it the bug. Output that only shows
the program runs, or shows the expected behavior, is not evidence of
the bug. A control run (the same steps with the trigger removed,
behaving correctly) strengthens the proof but is not required.

## Honesty

Where it lives:
- Eval: every sentence in the claim comment and the report that claims
  something: "reproduced", "confirmed", a root cause, a scope ("all
  versions", "every machine", "guaranteed"), and the result line.
- Live: the same in the drafts.

What good looks like: pair each claim with the artifact behind it. A
claim with no artifact behind it fails, and so does a claim that
describes an artifact as showing more than it shows (a garbled output
called a crash, a validation error called the reported panic). An
honest cannot reproduce is a pass: it says it did not reproduce, shows
the faithful attempt's output, and names what differed from the
issue's conditions. A cannot reproduce run on a different OS, shell,
or version than the issue is still honest and faithful when it says so
and does not claim the bug is absent in general. Expected vs actual stated backwards from what the
artifact shows is a failure.

## Comms

Where it lives:
- Eval: the claim comment, read against the Issue section; the repo
  facts block's contribution policy line (AI policy) and bug report
  line (template asks), read against both comments.
- Live: the claim draft against the issue on GitHub; the repo's
  `CONTRIBUTING.md` (and any AI policy file) and issue templates in
  `.github/ISSUE_TEMPLATE/`. For Path Review, also `scope.md` house
  rules: classmates' claims do not block a claim, and a piggyback
  ("same as above") is never a repro.

What good looks like:
- Claim: names something only this issue has (the function, input,
  error, version) and a next step the author controls, promising an
  investigation or report. A +1, "assign me", a reservation request, a
  guaranteed fix, or a deadline fails.
- AI policy: treat every package as AI assisted work. Read the policy
  literally. "All AI usage must be disclosed" or a disclosure ask that
  covers issues or comments means a comment must say AI was used and to
  what extent; a policy that asks for disclosure only in pull requests,
  or that only asks for responsibility and understanding, does not
  require it here. A rule that comments be in the contributor's own
  words is met by specific first person writing. No stated policy:
  nothing required.
- Template asks: the fields the repo's bug template requests are
  present in substance, in any order.
