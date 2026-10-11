# Evaluation Results: Refund Policy Question

**Project:** LLM Response Evaluation & Factual Grounding  
**Evaluation type:** Practice exercise  
**Data status:** Synthetic source and constructed candidate responses

## 1. Task

**User question:** Can I return a product after 20 days, and how long will my refund take?

**Reference source:** `sample.txt`

The source policy states:

- Refunds may be requested within 14 calendar days of delivery.
- Products must be unused and returned in original packaging.
- Requests must include the order number.
- Approved refunds are processed within 5–7 business days after the returned product is received.
- Shipping-charge refundability is not specified.

## 2. Candidate responses

### Response A — Constructed practice response

> Yes, you can return the product within 30 days of delivery. The item must be unused and in its original packaging. Once the return is approved, your refund will be processed within 3–5 business days. Shipping charges are also refundable.

### Response B — Constructed practice response

> According to the policy, refund requests must be made within 14 calendar days of delivery, so a request after 20 days falls outside the stated window. The product must be unused, in its original packaging, and the request must include the order number. Approved refunds are processed within 5–7 business days after the returned product is received. The policy doesn't specify whether shipping charges are refundable.

## 3. Claim verification

| Claim                                                                           | Source evidence                                                            | Classification              |
| ------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | --------------------------- |
| Response A: returns are allowed within 30 days                                  | The policy says requests must be made within 14 calendar days of delivery. | Contradicted                |
| Response A: product must be unused and in original packaging                    | The policy explicitly states both conditions.                              | Supported                   |
| Response A: refund takes 3–5 business days                                      | The policy says 5–7 business days after the returned product is received.  | Contradicted                |
| Response A: shipping charges are refundable                                     | The policy does not specify shipping-charge refundability.                 | Not specified / unsupported |
| Response B: the refund window is 14 calendar days                               | The policy explicitly states 14 calendar days.                             | Supported                   |
| Response B: a request after 20 days is outside the stated window                | Twenty days is beyond the stated 14-day window.                            | Supported                   |
| Response B: original packaging, unused condition, and order number are required | The policy explicitly states these requirements.                           | Supported                   |
| Response B: approved refunds take 5–7 business days after receipt               | The policy explicitly states this timeline and trigger.                    | Supported                   |
| Response B: shipping refundability is unspecified                               | The policy contains no rule on shipping-charge refunds.                    | Supported                   |

## 4. Rubric scores

Each criterion is scored from 0 to 2 using `evaluation-rubric.md`.

| Criterion             | Response A | Response B | Rationale                                                                                                                           |
| --------------------- | ---------: | ---------: | ----------------------------------------------------------------------------------------------------------------------------------- |
| Factual correctness   |        0/2 |        2/2 | A gives incorrect return and processing timelines and an unsupported shipping-refund claim. B accurately reflects the source.       |
| Source grounding      |        0/2 |        2/2 | A contradicts or goes beyond the policy on material claims. B's material claims are supported by the policy.                        |
| Instruction-following |        1/2 |        2/2 | A attempts to answer both parts but gives misleading information. B directly answers the return-window and refund-timing questions. |
| Completeness          |        1/2 |        2/2 | A omits the order-number requirement and gives incorrect policy details. B includes the key requirements and timing.                |
| Clarity               |        2/2 |        2/2 | Both responses are readable and easy to understand, even though A is factually unreliable.                                          |
| **Total**             |   **4/10** |  **10/10** | **Response B is preferred.**                                                                                                        |

## 5. Comparative judgment

**Preferred response: B**

Response B is preferable because it answers the question using the source policy and preserves the stated conditions and timeline. Response A contains material factual errors: it changes the refund request window from 14 to 30 days, changes the processing estimate from 5–7 to 3–5 business days, and asserts that shipping charges are refundable even though the source does not address that issue.

The shipping-charge claim is best classified as **unsupported / not specified**, rather than directly contradicted: the policy is silent on that point. By contrast, the 30-day return window and 3–5 business-day processing time directly conflict with the stated policy.

Response A is still clear, which is why its clarity score remains 2/2. This illustrates why evaluation dimensions should be scored separately rather than allowing factual errors to automatically determine every score.

## 6. Limitations

- This is one small, manually scored exercise using a synthetic policy.
- The candidate responses were constructed for practice and were not collected from real model runs.
- The scores reflect application of this project's custom rubric; they do not establish general model quality or evaluator agreement.
- A larger evaluation should use more tasks, a documented sampling method, and ideally independent reviewers to assess scoring consistency.

## 7. Skills demonstrated

- Source-based factual verification
- Identification of contradicted and unsupported claims
- Rubric-based response scoring
- Comparative response ranking
- Evidence-based written justification
- Distinguishing factual correctness from clarity
