# PyPI Text Conversational — TOPSIS Model

**Student:** Sameer  
**Roll No:** 102316089  
**Task Category:** Text Conversational (PyPI Models)  

---

## Table of Contents

1. Overview  
2. Methodology (TOPSIS)  
3. Models Evaluated  
4. Evaluation Metrics  
5. Weight Scenarios  
6. Results & Key Findings  
7. Environment Setup  
8. License  

---

## Overview

This project benchmarks multiple **pre-trained conversational models available via PyPI (Hugging Face Transformers)** and ranks them using **TOPSIS (Technique for Order Preference by Similarity to Ideal Solution)**.

Instead of selecting a model based on a single performance metric, a **multi-criteria decision-making (MCDM)** approach is used to evaluate models based on:

- Response quality
- Diversity
- Inference speed
- Memory/size efficiency

The objective is to identify the model that provides the **best balance between conversational performance and computational cost**.

This approach follows a scientific model selection strategy similar to the methodology described in the project reference. :contentReference[oaicite:0]{index=0}

---

## Methodology (TOPSIS)

TOPSIS ranks alternatives based on their distance from:

- **Ideal Best Solution** (maximum benefit, minimum cost)
- **Ideal Worst Solution**

### Steps

1. Construct the decision matrix  
2. Normalize the matrix (vector normalization)  
3. Apply criteria weights  
4. Determine ideal best and ideal worst values  
5. Compute Euclidean distances from both ideals  
6. Calculate the **closeness coefficient**  
7. Rank models (higher score = better)

TOPSIS ensures balanced decision-making across multiple performance criteria.

---

## Models Evaluated

| Model | Source | Type |
|------|-------|------|
| DialoGPT-small | microsoft/DialoGPT-small | Causal conversational model |
| BlenderBot-small | facebook/blenderbot_small-90M | Seq2Seq chatbot |
| GPT-2 (Chat) | gpt2 | General LM used conversationally |

These models were selected because they:
- Are publicly available via PyPI
- Represent different architectures
- Provide a mix of performance vs efficiency trade-offs

---

## Evaluation Metrics

Each model was tested on multiple prompts and evaluated using:

| Metric | Type | Description |
|--------|------|------------|
| Avg Response Length | Benefit | Measures informativeness |
| Distinct-1 | Benefit | Unigram diversity |
| Distinct-2 | Benefit | Bigram diversity |
| Inference Time (s) | Cost | Total generation time |
| Model Size (MB) | Cost | Memory requirement |

**Benefit metrics:** Higher is better  
**Cost metrics:** Lower is better  

---

## Weight Scenarios

Three decision scenarios were tested:

### 1. Balanced
Equal importance to quality and efficiency.

| Metric | Weight |
|--------|-------|
| Length | 0.20 |
| Distinct-1 | 0.20 |
| Distinct-2 | 0.20 |
| Time | 0.20 |
| Size | 0.20 |

---

### 2. Quality Priority
Focus on conversational richness.

| Metric | Weight |
|--------|-------|
| Length | 0.30 |
| Distinct-1 | 0.30 |
| Distinct-2 | 0.30 |
| Time | 0.05 |
| Size | 0.05 |

---

### 3. Speed Priority
Focus on deployment efficiency.

| Metric | Weight |
|--------|-------|
| Length | 0.05 |
| Distinct-1 | 0.05 |
| Distinct-2 | 0.05 |
| Time | 0.50 |
| Size | 0.35 |

---

## Results & Key Findings

Outputs generated:

- `topsis_results.csv` — Model metrics and rankings  
- `topsis_plot.png` — TOPSIS score comparison  
- `sample_responses.csv` — Example outputs from each model  

### Observations

- Larger models generally produce richer responses but are slower.
- Smaller models offer faster inference and lower memory usage.
- The best model depends on deployment requirements:
  - **Quality scenario:** conversational richness dominates
  - **Speed scenario:** lightweight models rank higher
  - **Balanced scenario:** provides the most practical recommendation

TOPSIS enables selecting the **most suitable model for real-world constraints**, not just the most powerful one.

---
