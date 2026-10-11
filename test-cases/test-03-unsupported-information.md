# Test 3: Unsupported Claims and Missing Information

## Objective

Evaluate whether the model recognizes when the reference policy does not contain enough information to answer a question, rather than guessing or inventing details.

## Reference Source

Use `sample.txt` as the sole source of truth. Do not assume rules that are not stated in that document.

## Instructions to the Model

Answer each question using only the reference policy. For each item, state what the policy explicitly says and whether the requested detail is specified. If it is not specified, say so clearly. Do not infer a policy from common business practices.

## Questions

1. What percentage of refund requests are approved?
2. Are shipping charges automatically refunded?
3. Does the policy allow extensions beyond the 14-calendar-day request window?
4. Is an expedited refund option available, and does it involve an additional fee?
5. Does the policy state that refunds are returned to the original payment method?

## Evaluation Notes

Score the response using `evaluation-rubric.md`. Check that the model does not invent percentages, refund methods, exceptions, expedited services, or fees. Keep the original model output unchanged in the corresponding file under `responses/`. Record scores and evidence-based explanations in `evaluation-results.md`.
