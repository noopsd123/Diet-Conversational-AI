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

Base Model : google/flan-t5-large
Parameters : 750M
Task Type : Seq2Seq (Text-to-Text Generation)
Input : Dietary question (natural language prompt)
Output : Nutritional advice response

Before vs After Fine-Tuning
Question: What is a good source of iron for a vegetarian?

## Stage	Model Response
Before (base)	
"Iron can be found in adobe bricks and red paint."
After (fine-tuned)	
"Lentils, spinach, tofu, and fortified cereals are excellent iron sources for vegetarians."

##  Project Structure
diet-conversational-ai/
│
├── data/
│   └── dietary_qa_dataset.json      # 100-entry curated Q&A dataset
│
├── notebooks/
│   └── flan_t5_finetuning.ipynb     # Full training notebook
│
├── model/
│   └── flan_t5_diet_finetuned/      # Saved model weights
│
├── logs/
│   └── wandb/                       # W&B training run logs
│
├── requirements.txt
└── README.md
