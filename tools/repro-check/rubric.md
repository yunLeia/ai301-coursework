# Rubric: is this reproduction package ready to post?

Every check reads the thing itself against the issue, never the shape of
the write up. A terse report can pass every check; a long, confident,
well formatted one can fail them. Locations named below are defined in
`references/evidence-guide.md`.

Checks marked (claim) read only the claim comment or the repo facts, so
they run on a claim only draft. Every other check needs the repro
report; on a claim only draft it is graded `unclear` with evidence
`not yet applicable: claim-only draft` and is left out of the verdict.

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env_recorded | The repro report's environment record (Environment), read against the issue's stated target (versions, OS, build, config it names) and the repo's bug template asks. | The report names the software version it ran AND the platform, AND names every environment variable the issue itself says matters (OS, driver, backend, build profile, shell, runtime version). Fails if there is no environment record, or if a variable the issue ties the bug to is missing. | required |
| steps_rerunnable | The repro report's steps (Steps), read as a stranger who has only the public repo and the package text. | A stranger can go from a stated starting state to the trigger using only what the package shows. The command that fires the bug is shown exactly. Inputs and config are quoted, or described precisely enough to recreate them without guessing (for example "a minimal env.yml with a valid dependencies list plus a category section"). Fails if any step depends on something the reader cannot get (a private repo, an unshared config or file, "set up the project" with no commands), or if the step that fires the bug is missing. | required |
| trigger_faithful | The steps and environment (Steps, Environment) read against the issue's described trigger (Issue context: the exact input, syntax, flag, config, and version it reports). | The run exercises the issue's own trigger: same input or syntax, same code path, the version the issue targets or a stated one. Any deviation from the issue's conditions (older or newer version, different OS or shell, changed input) is named in the report. A disclosed environment deviation passes, including in a cannot reproduce, as long as the report scopes its result to its own environment. Fails if the steps swap in a different input or syntax, or silently run a different version or platform than the issue targets without saying so. | required |
| behavior_matches | The artifacts (Behavior shown: output excerpts, logs, exit codes, error names, observed values) read against the specific behavior the issue describes. | For a reproduction: an artifact shows the issue's own symptom (same error type or message, same wrong value, same crash vs non crash, same exit behavior). An adjacent symptom (a different error, a graceful validation message where the issue reports a crash, output showing the program merely runs) fails. For a cannot reproduce: an artifact shows what the attempt actually produced, and the report names what differed from the issue's conditions; that passes even though the artifact does not show the bug. Fails if there is no artifact at all, or if a non reproducing artifact is presented as the bug. | required |
| claims_backed | Every claim in the claim comment and the report (reproduced, root cause, scope such as "all versions" or "every machine", certainty words) paired with the artifact that backs it (Honesty). | Each claim is no stronger than a shown artifact supports. A cannot reproduce passes when it states what was tried, shows the result, and names what differed from the issue's conditions. Fails if the package asserts a reproduction, a cause, or a scope that no shown artifact supports, or narrates an artifact as showing something it does not. | required |
| claim_specific (claim) | The claim comment (Comms), read against the issue. | The claim names something specific to THIS issue (the behavior, function, file, input, or version) so it could not be pasted onto another issue, AND states what the author will do next. It promises investigation or a report, never a fix, a deadline, or a guarantee. Fails on a bare +1, "assign me", reservation requests, or boilerplate interchangeable across issues. | required |
| ai_policy_respected (claim) | The repo facts contribution policy (Comms: AI policy), read against both comments. Treat every package as AI assisted work. | If the policy requires disclosing AI use for issue comments or for all AI use in any form, at least one comment discloses it (the tool or assistance and its extent). If the policy requires comments in the contributor's own words, the comments read as specific first person writing, not generic generated text. If the policy states no AI rule, or asks for disclosure only in pull requests, this passes. | required |
| template_asks | The repo facts bug template asks, read against the report. | The report supplies the fields the template asks for (for example expected vs actual), or the equivalent information, in any order. | preferred |

## Verdict rule

accept if every required check passes. Preferred checks never change
the verdict. `unclear` counts as fail, except the claim only case above,
where checks that need the repro report are graded `unclear` with
`not yet applicable: claim-only draft` and do not count. On a claim only
draft the verdict answers only whether the claim comment is ready to
post: accept if `claim_specific` and `ai_policy_respected` both pass.
