# LLM Healthcare Reasoning Pipeline

Applying LLM prompting strategies on synthetic EHR data (Synthea) for clinical text generation, disease classification, and note simplification.

## Overview

This project builds an end-to-end pipeline using GPT-5-mini to process structured healthcare data and evaluate multiple LLM reasoning methods:

- **Zero-Shot**: Direct prompting without examples
- **Few-Shot (ICL)**: In-Context Learning with examples
- **Chain-of-Thought (CoT)**: Step-by-step reasoning
- **Tree-of-Thought (ToT)**: Multi-path exploration
- **Self-Consistency (SC-3)**: Majority voting across multiple outputs

### Tasks Performed

1. **Table → Clinical Snapshot Generation**: Convert structured patient data into natural language clinical summaries
2. **Diabetes Classification**: Classify patients as `yes` / `no` / `unsure` for diabetes risk
3. **Clinical Note Simplification**: Transform complex medical notes into patient-friendly language

All experiments use **Synthea synthetic patient data** (no PHI/protected health information).

## Key Features

- **Structured-to-text LLM generation** with validation for:
  - Unit consistency (e.g., mg/dL, mmol/L)
  - Hallucination detection
  - Fabricated field identification
  
- **Reasoning-aware classification** with:
  - Clinical decision rules
  - Majority-vote self-consistency

- **Readability and Jargon evaluation** using:
  - Flesch-Kincaid readability scores
  - Custom healthcare jargon metrics

- **Healthcare-specific logic** including:
  - A1C thresholds for diabetes
  - ICD-10 code detection
  - BMI and LDL cholesterol analysis

## Results Summary

### Diabetes Risk Classification (N = 60)

| Metric | Score |
|--------|-------|
| **F1 Score** | 65.6% |
| **Recall** | 100% |
| **Coverage** (non-"unsure") | 83.3% |

### Simplification Task

| Metric | Result |
|--------|--------|
| **Readability Improvement** | 71% |
| **Jargon Reduction** | 0.3% (post-simplification) |

### Clinical Snapshot Generation

Evaluated for:
- Hallucination detection
- Unit consistency
- Clinical readability
- Completeness of information

## Tech Stack

- **Languages**: Python
- **Data Processing**: Pandas, NumPy
- **Templating**: Jinja2
- **Visualization**: Matplotlib
- **Evaluation**: Scikit-learn
- **LLM**: OpenAI GPT-5-mini
- **Dataset**: Synthea synthetic healthcare data
