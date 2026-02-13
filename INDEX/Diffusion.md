# Diffusion Models Index

## Purpose

This file tracks papers that use or extend **Diffusion Models**.

Diffusion is a **model family**, not a primary contribution category.  
Therefore, papers listed here must also belong to exactly **one** main folder in `PAPERS/`.

This file answers:

> "Which papers in this repository involve diffusion models?"

It does NOT replace primary classification.

---

## Core Concept

Diffusion models learn data distributions by:

1. Gradually adding noise (forward process)
2. Learning to reverse that noise (denoising process)
3. Sampling by iterative refinement

Key properties:
- Iterative generation
- Score-based learning
- Probabilistic formulation
- Often trained with noise prediction objective

---

## Canonical Foundations

- DDPM (Denoising Diffusion Probabilistic Models)
- Score-based Generative Modeling
- DDIM
- Latent Diffusion
- Diffusion Transformers

(Foundational papers are typically stored in `99_Surveys_Tutorials/`
or `05_Theory_Math/` depending on emphasis.)

---

## Diffusion Variants Observed in This Repo

### 1. Standard Pixel Diffusion
- Image generation
- Reconstruction
- Inpainting

### 2. Latent Diffusion
- Operates in VAE latent space
- Memory efficient
- Common in large-scale models

### 3. Conditional Diffusion
- Text-conditioned
- Class-conditioned
- Identity-conditioned
- Task-conditioned

### 4. Discriminative Use of Diffusion
- Feature extraction
- Anomaly detection
- Face Anti-Spoofing
- Representation learning

### 5. Hybrid Models
- Diffusion + Transformer
- Diffusion + GAN
- Diffusion + Contrastive learning

---

## Papers Using Diffusion

| Paper | Year | Primary Folder | Usage Type | Notes |
|-------|------|----------------|------------|-------|
| TBD   |      |                |            |       |

(Each paper must be stored elsewhere.  
This table only references them.)

---

## When to Add a Paper Here

Add a paper if:

- Diffusion is central to the method
- Diffusion is modified or extended
- Diffusion is used as feature backbone
- Diffusion defines the training objective

Do NOT add if diffusion is only mentioned in related work.

---

## Cross-Reference Rules

Every diffusion paper should:

1. Be stored in exactly one primary folder:
   - `01_Loss_Objective/`
   - `02_Architecture/`
   - `03_Training_Strategy/`
   - `04_Dataset_Protocol/`
   - `05_Theory_Math/`
   - `99_Surveys_Tutorials/`

2. Be linked back here manually in the table.

---

## Folder vs Index Reminder

Folders answer:
> "What is this paper's main contribution?"

Indexes answer:
> "Which conceptual family does this paper belong to?"

Diffusion is a conceptual family.

---

## Maintenance Rule

- Update when a diffusion paper is added.
- Review quarterly for outdated entries.
- Keep the table minimal and structured.

---

## Final Principle

Diffusion is a tool.  
Classification is about contribution.
