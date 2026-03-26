# Video Understanding Index

## Purpose

This file tracks papers related to **Video Understanding**.

Video Understanding is a **task**, not a primary contribution category.  
All papers listed here must also belong to exactly one folder in `PAPERS/`.

This file answers:

> "Which papers in this repository are related to video understanding?"

It does NOT replace primary classification.

---

## What is Video Understanding?

Video Understanding refers to learning representations from video data to perform tasks such as:

- Action recognition
- Temporal event understanding
- Video classification
- Spatio-temporal feature learning

Key challenge:
> Modeling both **spatial (appearance)** and **temporal (motion)** information.

---

## Core Evolution of Video Understanding

### 1. Handcrafted & Motion-based Features
- Explicit motion modeling using optical flow or trajectories

### 2. Two-Stream & Early Deep Learning
- Separate spatial and temporal streams

### 3. 3D Convolutional Networks
- Joint spatio-temporal modeling

### 4. Efficient Temporal Modeling
- Lightweight temporal reasoning

### 5. Transformer-based Video Models
- Long-range temporal dependency modeling

---

## Papers

| Paper | Year | Primary Folder | Category | Key Idea | Notes |
|-------|------|----------------|----------|----------|-------|
| Two-Stream ConvNet | 2014 | 02_Architecture/Backbone | Two-Stream | RGB + Optical Flow | Early deep video model |
| LRCN | 2015 | 02_Architecture/Backbone | CNN + RNN | CNN + LSTM | Sequential modeling |
| C3D | 2015 | 02_Architecture/Backbone | 3D CNN | Spatio-temporal conv | First unified 3D conv |
| iDT | 2016 | 03_Training_Strategy | Handcrafted | Improved trajectories | Pre-deep baseline |
| TSN | 2016 | 03_Training_Strategy | Temporal Sampling | Sparse segment sampling | Efficient long video |
| I3D | 2017 | 02_Architecture/Backbone | 3D CNN | Inflated 2D ConvNet | Strong baseline |
| SlowFast | 2019 | 02_Architecture/Backbone | Multi-pathway | Slow + Fast streams | Motion vs semantics |
| TSM | 2019 | 03_Training_Strategy | Temporal Shift | Channel shift | Zero FLOPs temporal modeling |
| ViViT | 2021 | 02_Architecture/Backbone/Transformer | Transformer | Pure video transformer | Global attention |
| VTN | 2021 | 02_Architecture/Backbone/Transformer | Transformer | Video Transformer Network | Sequence modeling |
| TimeSformer | 2021 | 02_Architecture/Backbone/Transformer | Transformer | Divided attention | Efficient attention |
| Video Swin Transformer | 2022 | 02_Architecture/Backbone/Transformer | Transformer | Hierarchical window attention | Scalable video model |

---

## Sub-Directions

### Spatial-Temporal Modeling
- 3D CNN
- Two-stream networks

### Temporal Efficiency
- TSN
- TSM

### Transformer-based Modeling
- ViViT
- TimeSformer
- Video Swin

### Hybrid Models
- CNN + RNN
- CNN + Transformer

---

## When to Add a Paper

Add a paper if:

- The main task is video understanding (e.g., action recognition)
- The method explicitly models temporal information
- Video representation learning is a core contribution

Do NOT add if:

- Video is only used as input without temporal modeling
- The focus is unrelated (e.g., pure image-based task)

---

## Folder vs Index Reminder

Folders answer:
> "What is the paper’s primary contribution?"

This index answers:
> "Is this paper related to video understanding?"

Task ≠ Contribution.

---

## Maintenance Rule

- Update when a new video paper is added
- Keep categories consistent
- Avoid duplicating classification logic

---

## Final Principle

Video Understanding is a task.

Contribution defines classification.