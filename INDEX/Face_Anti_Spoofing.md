# Face Anti-Spoofing (FAS) Index

## Purpose

This file tracks papers related to **Face Anti-Spoofing (FAS)**.

Face Anti-Spoofing is a **task**, not a primary contribution category.

Therefore:
- Papers listed here must also belong to exactly one main folder in `PAPERS/`.
- This file exists for task-level navigation only.

This file answers:

> "Which papers in this repository work on Face Anti-Spoofing?"

It does NOT determine classification.

---

## What is Face Anti-Spoofing?

Face Anti-Spoofing (FAS) aims to detect whether a presented face is:

- Bona fide (real, live person)
- Attack (spoof attempt)

Typical attack types:
- Print attack
- Replay attack
- 3D mask attack
- Deepfake / digital injection
- Partial attacks

FAS is a binary or multi-class classification problem,
but often evaluated under cross-domain or cross-dataset settings.

---

## Common Research Directions in FAS

### 1. Texture-Based Methods
- Micro-texture analysis
- Frequency domain features
- LBP-like handcrafted descriptors

### 2. Depth / rPPG-Based Methods
- Depth estimation
- Remote photoplethysmography (rPPG)
- Physiological signal modeling

### 3. Learning-Based Approaches
- CNN-based classification
- Vision Transformer
- Hybrid CNN-Transformer

### 4. Domain Generalization
- Cross-dataset robustness
- Domain adaptation
- Meta-learning
- Style normalization

### 5. Generative Modeling in FAS
- Diffusion-based modeling
- Reconstruction-based detection
- Anomaly detection
- Synthetic spoof generation

### 6. Multi-Modal FAS
- RGB + Depth
- RGB + IR
- RGB + rPPG
- Audio-visual anti-spoofing

---

## Evaluation Protocols Commonly Used

- Intra-dataset evaluation
- Cross-dataset evaluation
- Leave-one-domain-out
- Open-set spoof detection

Typical metrics:
- APCER
- BPCER
- ACER
- AUC
- HTER

---

## Datasets Frequently Used

- CASIA-FASD
- Replay-Attack
- OULU-NPU
- SiW
- SiW-M
- MSU-MFSD
- WMCA
- CelebA-Spoof

(Datasets are tracked in `04_Dataset_Protocol/` when they are the main contribution.)

---

## Papers Related to FAS

### Architecture-based FAS

| Paper | Year | Primary Folder | Core Contribution | Notes |
|-------|------|----------------|------------------|-------|
| TBD   |      |                |                  |       |

### Loss-based FAS

| Paper | Year | Primary Folder | Core Contribution | Notes |
|-------|------|----------------|------------------|-------|
| TBD   |      |                |                  |       |

### Domain Generalization FAS

| Paper | Year | Primary Folder | Core Contribution | Notes |
|-------|------|----------------|------------------|-------|
| TBD   |      |                |                  |       |

Each paper must:
- Be stored in exactly one primary folder.
- Be referenced here manually.

---

## When to Add a Paper Here

Add a paper if:

- The main task is Face Anti-Spoofing.
- The method is evaluated primarily on FAS benchmarks.
- FAS is central, not secondary.

Do NOT add if:
- FAS is a minor experiment.
- The paper focuses on general face recognition without spoof detection.

---

## Folder vs Index Reminder

Folders answer:
> "What is the paper’s primary contribution?"

This index answers:
> "Does this paper work on Face Anti-Spoofing?"

Task ≠ Contribution.

---

## Maintenance Rule

- Update whenever a FAS paper is added.
- Review quarterly.
- Keep entries structured and minimal.

---

## Final Principle

Face Anti-Spoofing is a task.

Contribution defines classification.
