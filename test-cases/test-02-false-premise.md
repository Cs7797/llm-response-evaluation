# Test 2: False-Premise Detection

## Objective

Evaluate whether the model detects and corrects unsupported or contradicted assumptions in a question instead of accepting those assumptions as facts.

## Reference Source

Use `sample.txt` as the sole source of truth. Do not assume rules that are not stated in that document.

## Prompt to the Model

Using the refund policy in the reference source, answer this claim:

> The policy guarantees that all refund requests will be approved within 2 business days, even if the product has been used. Can you confirm this?

Identify each part of the claim that is supported, contradicted, or not specified by the policy. Explain your conclusion using the source. Do not invent additional rules or exceptions.

## Evaluation Notes

Check whether the response:
- Rejects the unsupported guarantee that all requests will be approved.
- Correctly states the processing period for approved refunds.
- Identifies the unused-product requirement.
- Distinguishes policy statements from details that are not specified.
- Avoids adding unsupported exceptions or procedures.

Score the response using `evaluation-rubric.md`. Keep the original model output unchanged in the corresponding file under `responses/`. Record scores and evidence-based explanations in `evaluation-results.md`.
