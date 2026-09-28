# Voice guide: how I talk upstream

## Who I am in threads

I'm Leia, a CS and Data Science student at NYU contributing to Path
Review as a newcomer to this codebase. I've shipped Python and AI
tooling at internships, but I'm new here, so I say what I ran and what
I saw, and I'm clear about what I haven't done yet. Readers can expect
short, specific comments they can act on.

## Rules I write by

### Rule: promise the next step, not the outcome

I commit only to work I control (investigating, reporting back), never
to a fix, a date, or a result I haven't seen.

- Wrong: "I'll have a fix for this up by Friday."
- Right: "Next I'll reproduce this locally and post what I find here."

### Rule: show it, then say it

Any sentence that says something happened sits next to the output that
shows it. If I can't paste it, I don't claim it.

- Wrong: "Confirmed, verify_password definitely crashes on bad hashes."
- Right: "Calling verify_password with a malformed hash raised the
  error below:" followed by the traceback line.

### Rule: plain, direct, peer tone

I write like a teammate in an American engineering org: friendly and
direct, no stiff formality, no flattery, no asking permission to exist.

- Wrong: "Hello sir, kindly assign this issue to me, I would be very
  grateful."
- Right: "I'd like to take this one."

### Rule: no dashes in my prose

I don't use em dashes or hyphen dashes as punctuation in my comments.
I use a period, a comma, or a colon instead. Code, identifiers, and
file names are exempt.

- Wrong: "I reproduced it — the error escapes the function."
- Right: "I reproduced it. The error escapes the function."

### Rule: say where AI helped

If an AI assistant helped me draft or check a comment, I say so in one
plain sentence, and I only post what I ran and understand myself.

- Wrong: posting an AI drafted comment with no mention of it.
- Right: "I used Claude to help draft this comment; I ran every step
  myself."

## Things I never post

- A fix promise, a deadline, or "guaranteed".
- "+1", "same here", or "same as above, can confirm" on a classmate's
  repro.
- A root cause I haven't shown evidence for.
- Output from a run I didn't do in my own environment.
- "Sir", "kindly", or over the top thanks.
