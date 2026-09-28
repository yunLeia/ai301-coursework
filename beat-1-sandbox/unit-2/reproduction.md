# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

yunLeia

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5863745162

Hi, I'd like to take this one as a first contribution. I haven't reproduced it yet. Next I'll set up the repo following docs/SETUP.md and call `verify_password` with the `not_a_valid_bcrypt_hash` input from the xfail test (manifest H-05) to check whether passlib's `UnknownHashError` escapes instead of it returning `False`. I'll post a repro report here with my environment, steps, and output, whether or not it reproduces.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72#issuecomment-5863919217

Reproduced: `verify_password` in core/security.py raises `passlib.exc.UnknownHashError` for a malformed stored hash instead of returning `False`.

**Environment:** fork of this repo at commit 2f4e82f, macOS 27.0 (arm64), Python 3.11.0, passlib 1.7.4, bcrypt 4.3.0, installed with `pip install -e ".[dev]"`. No Docker services needed, since this calls core/security.py directly.

**Steps** (from a fresh clone of my fork):

```
git clone https://github.com/yunLeia/pathreview-ai301-fa26-s3.git
cd pathreview-ai301-fa26-s3
git checkout 2f4e82f
python3 -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
cp .env.example .env
python -c "from core.security import verify_password; print(verify_password('password', 'not_a_valid_bcrypt_hash'))"
```

**Actual** (last line of the traceback):

```
passlib.exc.UnknownHashError: hash could not be identified
```

An empty string as the stored hash gives the same error:

```
python -c "from core.security import verify_password; print(verify_password('password', ''))"
passlib.exc.UnknownHashError: hash could not be identified
```

**Control** (valid bcrypt hash, same function, works as expected):

```
python -c "from core.security import verify_password, hash_password; h = hash_password('password'); print(verify_password('password', h), verify_password('nope', h))"
True False
```

**Covering test:** with the xfail marker ignored, the H-05 test fails:

```
python -m pytest tests/unit/test_security.py -k test_verify_with_wrong_hash_format --runxfail
FAILED tests/unit/test_security.py::TestSecurity::test_verify_with_wrong_hash_format
1 failed, 24 deselected, 2 warnings in 0.64s
```

**Expected:** `verify_password` returns `False` for a malformed stored hash (fail closed), as the issue and the test describe.

**Notes:**
- Every import also prints a `(trapped) error reading bcrypt version` traceback (`AttributeError: module 'bcrypt' has no attribute '__about__'`). passlib catches it internally, the control still returns `True False`, so it's unrelated to this bug.
- A hash with a bcrypt prefix but a truncated body raises a plain `ValueError` instead of `UnknownHashError`:

  ```
  python -c "from core.security import verify_password; print(verify_password('password', '\$2b\$12\$tooshort'))"
  ValueError: salt too small (bcrypt requires exactly 22 chars)
  ```

  That's outside this issue's wording, but a fail closed fix probably needs to handle it too.

## Eval iterations

**Run history**

1. Full run: 18/20 scored items, bar PASS. Misses: pkg-05 (gold accept, graded reject on steps_rerunnable) and pkg-10 (gold accept, graded reject on trigger_faithful and behavior_matches). Categories: clear-accept 6/8, disclosure 1/1, no-evidence 4/4, unfollowable-comms 3/3, wrong-target 4/4.
2. Partial run after revising steps_rerunnable, trigger_faithful, behavior_matches and the evidence guide: `--only pkg-05,pkg-10,pkg-16,pkg-18,pkg-06,pkg-20,calib-04 --include-calibration`. 6/6 scored items agreed (calib-04 also agreed, unscored). Both misses fixed, every canary held.
3. Confirming full run, saved with `--save-run eval-run.txt`: 20/20 scored items, bar PASS, every category matched (clear-accept 8/8, disclosure 1/1, no-evidence 4/4, unfollowable-comms 3/3, wrong-target 4/4).

**Package analysis**

pkg-10 (starship/starship#7648). In run 1 my rubric decided reject; the gold label is accept. The report is an honest cannot reproduce: the issue was filed on macOS with fish 4.7.1, and the author ran the exact symlink layout and config on Ubuntu 24.04 with zsh 5.9, showed the prompt that rendered fine, and named both differences plus a hypothesis for why fish's PWD handling might matter. My first trigger_faithful said the run must exercise the issue's own trigger on the version the issue targets, and behavior_matches asked for "the faithful attempt". The grader read a run on a different OS and shell as not faithful, so both checks failed, even though the report disclosed every deviation and scoped its result to its own machine. The gold label treats that as the honest outcome phase 2 asks for. After I made both checks say a disclosed environment deviation passes when the result is scoped to that environment, pkg-10 graded accept in runs 2 and 3.

**Check rationale**

| trigger_faithful | The steps and environment (Steps, Environment) read against the issue's described trigger (Issue context: the exact input, syntax, flag, config, and version it reports). | The run exercises the issue's own trigger: same input or syntax, same code path, the version the issue targets or a stated one. Any deviation from the issue's conditions (older or newer version, different OS or shell, changed input) is named in the report. A disclosed environment deviation passes, including in a cannot reproduce, as long as the report scopes its result to its own environment. Fails if the steps swap in a different input or syntax, or silently run a different version or platform than the issue targets without saying so. | required |

My first version ended at "is named in the report" and failed on "silently run a different version or platform". That was right for pkg-16, which tested pandas 1.5.3 against a bug confirmed on latest without saying so, but it also held pkg-10, a cannot reproduce that named its OS and shell differences. The line that separates them is disclosure, not sameness: a report that says where it differs gives a maintainer something to act on, and one that hides the difference gives them wrong evidence. So I added the sentence that a disclosed deviation passes when the report scopes its result to its own environment, and kept "without saying so" on the failure side so silent swaps still fail.

**Trade-offs**

Loosening trigger_faithful and steps_rerunnable could have flipped packages that agreed in run 1, so before the confirming run I re-ran canaries with `--only`: pkg-16 (silent version swap, must stay reject), pkg-18 (steps live in a private monorepo, must stay reject), pkg-06 (no environment record), and pkg-20 (the one disclosure package), plus calib-04 as a free trap. All stayed reject in run 2 and again in run 3. The cost I accept: a disclosed deviation now passes trigger_faithful even when the deviation probably explains the result, so a lazy cannot reproduce on the wrong platform can get through if it names the difference. I also kept env_recorded strict, so a package like calib-04, with a real panic and a control run but no environment record, is held; that call is defensible either way, and I chose the reject because a stranger cannot place the attempt.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
