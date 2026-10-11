# Test 1: Standard Policy Questions

## Objective

Evaluate whether each model answers routine questions accurately using the reference refund policy, follows the stated requirements, and distinguishes explicit rules from details the policy does not specify.

## Reference Source

Use `sample.txt` as the sole source of truth. Do not assume rules that are not stated in that document.

## Instructions to the Model

Answer each question using only the reference policy. For every answer, explain the relevant policy condition briefly. If the policy does not provide enough information to answer a question, state that the information is not specified. Do not invent exceptions, guarantees, or procedures.

## Questions

1. A customer requests a refund 10 days after delivery. Is the request within the stated time limit, and what other stated conditions apply?
2. A customer requests a refund 20 days after delivery. Is the request within the stated time limit?
3. What information must a refund request include?
4. How long does an approved refund take to process, and when does that period begin?
5. Does the policy say whether shipping charges are refundable?
6. A customer opened the product packaging but says the product has not been used. Does the policy explicitly say whether opening the packaging alone makes the product ineligible?
7. A customer claims the policy guarantees that refunds will be processed within two business days. Is that claim supported by the policy?
8. A customer submits a refund request without an order number. What does the policy say about this, and does it describe any exception or alternative verification process?

## Evaluation Notes

Score the response using `evaluation-rubric.md`. Keep the original model output unchanged in the corresponding file under `responses/`. Record scores and evidence-based explanations in `evaluation-results.md`.
