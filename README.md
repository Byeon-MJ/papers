## 기여 유형 기준 분류
```
PAPERS/
├── INDEX/
├── 00_Inbox/
├── 01_Architecture/
├── 02_Loss_Objective/
├── 03_Training_Strategy/
├── 04_Dataset_Protocol/
├── 05_Theory_Math/
├── 99_Surveys_Tutorials/
└── README.md
```

논문의 주된 기여 형태에 따른 분류

- Architecture 기반
    - CNN → ViT, Hybrid, Attention 구조 변경

- Loss / Objective 기반
    - ArcFace, CosFace, SphereFace, Sub-center 계열

- Training Strategy 기반
    - Large batch, curriculum, sampler, augmentation

- Dataset / Protocol 기반
    - 새로운 데이터셋, cleaning, evaluation protocol

- Theoretical / Mathematical
    - 수식 해석, 수렴 분석, Bayesian 관점, geometry

### Architecture 기반 (Backbone / 구조)
```
01_Architecture/
├── CNN/
│   ├── ResNet/
│   ├── MobileNet/
│   └── EfficientNet/
├── ViT/
│   ├── Vanilla_ViT/
│   ├── Face_ViT/
│   └── Patch_Modification/
├── Hybrid_CNN_ViT/
├── Attention_Module/
│   ├── SE_CBAM/
│   └── Transformer_Block/
└── README.md
```

📌 기준:

- Loss는 기존 것 사용

- Backbone 구조 변경이 핵심 기여

- ViT-based Face Recognition 논문은 전부 여기

### Loss / Objective 기반
```
02_Loss_Objective/
├── ArcFace/
│   ├── 2019_ArcFace_AdditiveAngularMargin.pdf
│   ├── notes.md
│   └── experiments/
├── CosFace/
├── SphereFace/
├── SubCenter/
├── MetricLearning_General/
└── README.md
```

📌 여기에 들어갈 논문 기준:

- Loss 수식 자체가 핵심 기여

- margin, angle, decision boundary 변경

- face recognition의 “판별 기준”을 바꾸는 논문

📌 notes.md 내용:

- 수식 핵심

- Softmax 대비 차이

- Gradient 변화

- 실험에서 민감한 하이퍼파라미터

### Training Strategy 기반
```
03_Training_Strategy/
├── Large_Batch/
├── Sampler/
│   ├── PK_Sampler/
│   └── Class_Balanced/
├── Augmentation/
│   ├── RandAugment/
│   ├── Patch_Level/
│   └── Face_Specific/
├── Optimization/
│   ├── LR_Schedule/
│   └── Warmup/
└── README.md
```

📌 기준:

- 모델 구조/로스는 기존 것

- “어떻게 학습하느냐”가 성능을 좌우

-  실험 재활용 가치가 매우 큼 → 나중에 “성능 안 나올 때” 제일 먼저 다시 보는 폴더

### Dataset / Protocol 기반
```
04_Dataset_Protocol/
├── Dataset/
│   ├── MS1M/
│   ├── WebFace42M/
│   ├── Glint360K/
│   └── Custom_Cleaning/
├── Evaluation/
│   ├── LFW/
│   ├── CFP_FP/
│   ├── AgeDB/
│   └── IJB_BC/
├── Protocol_Design/
└── README.md
```

📌 기준:

- 데이터 정의 / 정제 / 평가 방식이 논문의 핵심

- 모델 성능보다 benchmark 신뢰도가 주제

- 실험 결과 해석할 때 근거 자료

### Theoretical / Mathematical 기반
```
05_Theory_Math/
├── Geometry/
│   ├── Angular_Margin_Geometry/
│   └── Hypersphere_Embedding/
├── Optimization_Theory/
│   ├── Convergence/
│   └── Stability/
├── Bayesian/
│   ├── Bayesian_View_of_DL/
│   └── Diffusion_Bayesian/
├── Information_Theory/
└── README.md
```

📌 기준:

- 실험보다 수식과 해석이 핵심

- 당장 구현 안 해도 “생각의 무기”가 되는 논문


## 파일 네이밍 규칙
```
[Year]_[Venue]_[FirstAuthor]_[ShortTitle].pdf

2020_CVPR_Deng_RetinaFace.pdf
2021_An_ViTFace.pdf
2023_Song_BayesianDiffusion.pdf
```

## Classification Rules
- Each paper is stored in ONE folder only.
- Classification is based on PRIMARY contribution.
- Model families (Diffusion, SAM, etc.) are tracked in /INDEX.
- Do NOT create model-name top-level folders.