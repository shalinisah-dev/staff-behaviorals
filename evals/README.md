# Behavioral Eval Specifications

The YAML files in this directory are portable behavior specifications, not an executable evaluation harness.

Each case defines:

- `input`: the scenario supplied to the skill;
- `required`: behaviors a passing response must demonstrate;
- `forbidden`: behaviors that cause failure;
- optional verdict constraints when calibration is part of the test.

## Manual or model-judge use

1. Run the case's `input` with the named skill enabled.
2. Compare the response semantically with every `required` and `forbidden` item.
3. Mark the case:
   - **Pass:** every required behavior appears and no forbidden behavior appears.
   - **Partial:** at least one required behavior is missing, with no forbidden behavior.
   - **Fail:** any forbidden behavior appears or the response misses the case's central requirement.
4. Record the exact output and judge rationale so regressions can be compared across skill revisions.

Do not grade on exact wording or headings. These cases test question matching, evidence discipline, calibration, and factual boundaries.

An executable runner is intentionally not claimed. A future runner should preserve this schema and make the model, judge, prompt, and pass threshold explicit.
