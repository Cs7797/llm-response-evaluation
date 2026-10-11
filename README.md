# LLM Response Evaluation: Factual Grounding and Instruction Following

A small, rubric-based evaluation project that examines how consistently large language models answer questions using a fixed reference document. The project focuses on factual correctness, source grounding, instruction-following, completeness, clarity, and the handling of unsupported information.

## Project Objectives

- Evaluate model responses against a defined source of truth.
- Check whether responses follow the source rather than inventing details.
- Test how models handle false premises and missing information.
- Apply the same scoring rubric to each model response.
- Document the evidence and reasoning behind the scores.

## Evaluation Setup

The current evaluation uses a fictional refund policy for an example store. The policy states that:

- Refund requests must be made within 14 calendar days of delivery.
- Products must be unused and returned in their original packaging.
- Refund requests must include an order number.
- Approved refunds are processed within 5–7 business days after the returned product is received.
- Shipping-charge refundability is not specified.

The fictional policy is the source of truth for the tests. Information not included in it should be treated as unspecified rather than inferred.

## Tests and Results

| Test | What it checks | ChatGPT GPT-6 | Google Gemini |
|---|---|---:|---:|
| Standard policy questions | Applying explicit rules and handling ambiguity | 9/10 | 7/10 |
| False-premise detection | Rejecting claims that conflict with the source | 10/10 | 10/10 |
| Unsupported claims and missing information | Recognizing details the source does not establish | 10/10 | 10/10 |

Scores are manual assessments of the specific responses recorded in this repository. The Gemini model version was not verified. These results are a small practice evaluation, not a general benchmark or a universal ranking of the models.

See [`evaluation-results.md`](evaluation-results.md) for the detailed findings and scoring rationale.

## Rubric

Responses are scored on five criteria, each from 0 to 2:

1. **Factual correctness** — Is the response factually consistent with the source?
2. **Source grounding** — Are claims supported by the source?
3. **Instruction-following** — Does the response follow the prompt's requirements?
4. **Completeness** — Does it address the question without omitting relevant information?
5. **Clarity** — Is the answer understandable and appropriately phrased?

Maximum score: **10 points per response**. The rubric is a custom rubric for this practice project, not a universal industry standard.

See [`evaluation-rubric.md`](evaluation-rubric.md) for the full scoring definitions.

## Repository Structure

```text
llm-response-evaluation/
├── README.md
├── sample.txt
├── evaluation-rubric.md
├── evaluation-results.md
├── test-cases/
│   ├── test-01-standard-policy-questions.md
│   ├── test-02-false-premise.md
│   └── test-03-unsupported-information.md
└── responses/
    ├── test-01-standard-policy-questions.md
    ├── test-02-false-premise.md
    └── test-03-unsupported-information.md
```

The `test-cases/` and `responses/` files are recommended organization for the prompts and raw model outputs. Create these folders and files as you add the test records; the detailed report and scores remain in `evaluation-results.md`.

## Where Questions and Model Responses Belong

Keep the test prompts separate from the model outputs so another person can reproduce the evaluation.

- **`test-cases/`** — Store the exact prompt sent to each model, the reference-source instructions, and the questions for that test. Preserve wording and question order.
- **`responses/`** — Store each model's full response exactly as generated. Label the model and, when known, its exact version. If the version is unknown, write `Version not verified`; do not guess.
- **`evaluation-results.md`** — Store score tables, evidence-based scoring explanations, comparisons, findings, and limitations.
- **`evaluation-rubric.md`** — Store the criteria and definitions used to assign scores.
- **`sample.txt`** — Store the fixed fictional policy used as the source of truth.

For fair comparisons, use the same prompt and reference text for each model in a test. Do not silently edit model outputs before scoring. If you need to correct a transcription error, keep the original output or clearly document the correction.

## How to Reproduce the Evaluation

1. Read `sample.txt` and treat it as the only source of truth for policy-specific answers.
2. Read `evaluation-rubric.md` before scoring.
3. Open a test prompt from `test-cases/`.
4. Submit the same prompt and reference policy to each model.
5. Save each full response in `responses/`, with the model name and version details where available.
6. Score the responses against the rubric and record the rationale in `evaluation-results.md`.

## Limitations

- The reference policy is fictional and intentionally small.
- The current evaluation covers three test scenarios and a limited number of questions.
- Scores were assigned manually by one reviewer; inter-rater agreement has not been measured.
- Results describe only the responses tested and should not be generalized to all tasks or model versions.

## Future Improvements

- Add more reference documents and question types.
- Include additional models and record exact model versions.
- Have a second reviewer score the same outputs and compare agreement.
- Add adversarial and multi-step questions.
- Track changes in results when prompts, models, or rubric definitions change.

## Purpose

This repository is a practical demonstration of structured LLM response evaluation, factual grounding, and rubric-based analysis. It emphasizes transparent criteria and documented reasoning rather than claiming a comprehensive model benchmark.
