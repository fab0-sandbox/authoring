---
name: s15-check
description: The work step of fab0 stage 15's routine check (pipeline skill-v15). Completes the step with the mark only this skill gives. Use only when a fab0 step's envelope, read with get_step through the fab0 connector, has with.skill equal to s15-check.
---

# s15-check

This skill is fab0 stage 15's routine check (AC15.11). It shows that a routine session reads the envelope's `with.skill` and uses the skill it names.

The session is working a fab0 step through the `fab0` connector, whose instructions it follows. It read the step with `get_step`, and the envelope's `with.skill` named this skill. Without a step id and the envelope `get_step` answers for it, stop: this skill runs only as a fab0 step. Never print the step id.

## Ask no one

This skill runs unattended in a routine. Never use AskUserQuestion or plan mode, and never wait for an answer. Change nothing in the repository or on GitHub.

## Finish

End the step with one call, `complete`, with the step id and:

- `outputs`: exactly `{ "mark": "s15-skill-read" }`;
- `usage`: the tokens each model used, summed from the session's transcript as the connector's instructions say, or `[]` only if you tried and couldn't learn them.

If `complete` is refused, `fail` the step with the refusal as its `reason` (at most 1,000 characters) and `usage`.
