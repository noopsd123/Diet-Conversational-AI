# Diet Conversational AI | LLM Fine-Tuning with Flan-T5-Large

General-purpose LLMs hallucinate dangerously on nutrition questions.
This project fine-tunes Google's Flan-T5-Large (750M parameters) on a
curated dietary Q&A dataset, reducing training loss by 44.8% across 3
epochs and shifting model responses from fabricated outputs to
nutritionally accurate dietary advice.

---

## Problem Statement

When asked nutrition questions, general-purpose LLMs like Flan-T5 out
of the box produce confident but dangerously incorrect answers —
fabricating food sources, inventing calorie counts, and mixing up
dietary protocols. No off-the-shelf model is tuned for health coaching.

This project solves that by fine-tuning Flan-T5-Large on a hand-curated
dietary Q&A dataset spanning 10+ nutrition domains, purpose-built to
adapt a general LLM into a reliable diet assistant.

---

## Key Results

| Metric                  | Value                        |
|-------------------------|------------------------------|
| Base Model              | Google Flan-T5-Large (750M)  |
| Training Dataset        | 100 dietary Q&A pairs        |
| Nutrition Domains       | 10+                          |
| Training Epochs         | 3                            |
| Initial Training Loss   | 28.42                        |
| Final Training Loss     | 15.69                        |
| Loss Reduction          | 44.8%                        |
| Optimizer               | AdamW + Linear Warmup        |
| Experiment Tracking     | Weights & Biases (W&B)       |

---

## Tech Stack

- **Model:** Google Flan-T5-Large (750M parameters) via HuggingFace Transformers
- **Framework:** PyTorch
- **Fine-Tuning:** HuggingFace Trainer API
- **Optimizer:** AdamW with linear warmup scheduling
- **Experiment Tracking:** Weights & Biases (W&B)
- **Dataset Format:** Structured JSON
- **Language:** Python

---

## Dataset

- 100 hand-curated dietary Q&A pairs in structured JSON format
- Covers 10+ nutrition domains including:
  - Calorie tracking
  - Keto diet
  - Intermittent fasting
  - Meal planning
  - Macronutrient breakdown
  - Protein sources
  - Micronutrients and deficiencies
  - Weight management
  - Gut health
  - Sports nutrition

Each entry follows a prompt-response format designed to teach the model
domain-specific dietary reasoning rather than generic health advice.

---

## Model Architecture

