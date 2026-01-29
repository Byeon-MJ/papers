# FLIP: Cross-domain Face Anti-spoofing with Language Guidance

> **Title :** FLIP: Cross-domain Face Anti-Spoofing with Language Guidance
> 
> 
> **Authors :** Koushik Srivatsan, Muzammal Naseer, Kartik Nandakumar
> 
> **Venue :** IEEE International Conference on Computer Vision (ICCV)
> 
> **Year :** 2023
> 
> **Task :** Face Anti-Spoofing, Cross-domain generalization, Vision-Language Models
> 
> **Keywords :** Face Anti-Spoofing, Cross-domain Generalization, Vision-Language Pre-training(VLP), CLIP, Language Guidance, Contrastive Learning, Vision Transformer(ViT)
> 

<aside>
💡

**안전한 Face Anti-Spoofing (FAS)을 위해서는 Cross-domain generalize performance가 필요한데 CLIP이라는 모델이 Vision task에서 generalization이 잘 된다고 하니, FAS에도 CLIP 모델을 활용하여 Robust Cross-domain generalize performance를 달성해보자.**

</aside>

## 1. Introduction - The Critical Need for Robust Face Anti-Spoofing (FAS)

### 왜 Face Anti-Spoofing (FAS)이 중요한가?

- **Face Recognition의 보편화**
    - 개인장치부터 공항 탑승 게이트 출입 통제, 금융 거래까지
    - 편리하고 비대면이라는 장점
- **취약점: Presentation Attacks**
    - 사진, 비디오 재생, 3D 마스크 등으로 신분을 위조하려는 시도
    - FAS 시스템의 보안을 무력화시키는 핵심 위협
- **결론:** 안전한 얼굴 인식 시스템을 위해 FAS는 필수이다

## 2. The Major Challenge: Cross-Domain Generalization

### 기존 FAS 방법들의 핵심적인 문제점 → 낮은 일반화 성능

- **Intra-domain vs Cross-domain**
    - **Intra-domain**: 학습 데이터와 동일한 환경(카메라, 조명, 위조 방식)에서는 높은 성능
    - **Cross-domain**: 학습에서 보지 못한 새로운 환경(카메라 센서, 조명 변화, 위조 도구, 환경 조건)에서는 성능이 급격히 저하
- **원인**
    - **Domain Gap**: 소스 도메인(학습 데이터)과 타겟 도메인(실제 환경) 간의 근본적인 분포 차이
    - **데이터 부족**: 실제 환경의 다양한 변화를 모두 커버할 만큼 충분한 학습 데이터 확보의 어려움
- **Prior Work Limitations**
    - **CNN 기반 방법**: 주로 지역적 특징(Local features)에 의존하여 전역적(global) 위조 패턴 파악에 한계
    - **ViT 기반 방법**: 장거리 의존성(long-range dependencies) 포착에 강점
        - 하지만 ImageNet 등 이미지 데이터로만 사전 학습된 ViT는 FAS 작업에 특화된 의미론적 이해가 부족
        - 추가적인 Adaptive modules나 도메인/공격 유형 정보를 요구하는 경우가 많아서 일반화 성능이 떨어짐

## 3. Core Idea: Leveraging Vision-Language Pre-training (VLP)

### FLIP 핵심 아이디어: Vision-Language Pre-trained (VLP) 모델 활용

- **VLP 모델이란? (e.g. CLIP)**
    - 수백만 개의 **이미지-텍스트 쌍**으로 사전 학습된 모델. (CLIP은 4억개의 이미지 쌍을 학습)
    - 이미지와 텍스트를 **동일한 임베딩 공간**에 매핑하는 능력 학습
    - 결과적으로 시각적 정보와 언어적 의미를 동시에 이해하고 표현
- **FLIP 프레임워크의 목표**
    - VLP 모델의 이미지 인코더로 FAS 모델을 Fine-tuning하여 일반 이미지 사전 학습 능력을 향상
    - VLP 모델의 텍스트 인코더를 사용하여 FAS 성능 향상에 기여
    - VLP 모델을 FAS에 적용할 때, **Self-supervised learning 기법**을 추가하여 일반화 능력을 더욱 향상

## 4. Introducing FLIP: The Framework Overview

### FLIP framework

- **Base model**: CLIP (Contrastive Language-Image Pre-training)
- 세 가지 Protocol 제안
    - **FLIP-Vision (FLIP-V)**: 사전 학습된 ViT의 이미지 인코더만 Fine-tuning 하고 MLP head를 추가.
    - **FLIP-Image-Text Similarity (FLIP-IT)**: FLIP-V에 텍스트 인코더를 추가하여 이미지 표현을 클래스별 텍스트 프롬프트 임베딩과 align 하여 분류
    - **FLIP-Multimodal-Contrastive-Learning (FLIP-MCL)**: FLIP-IT에 Multimodal contrastive learning을 추가하여 일반화 성능(Generalizability)을 극대화 → 최종 제안 기법
    
    ![image.png](attachment:a975e304-ee24-4593-adaf-c570a8038438:image.png)
    

### 4.1. FLIP-Vision (FLIP-V)

- **아이디어**: CLIP의 사전 학습된 ViT 이미지 인코더를 FAS task에 맞게 fine-tune
- **구조**
    - 입력 이미지 $I$ → CLIP ViT 이미지 인코더 $V$ → 최종 클래스 토큰 $c_K$ → ImageProj → Image representation $x$
    - $x$를 Multi-Layer Perceptro Classification head에 통과시켜 Real/Spoof 예측
- **학습**: 표준 Cross-Entropy Loss 사용
    
    $$
    L_{ce} = CrossEntropy(MLP(x), y_{true})
    $$
    
- **핵심**: CLIP 모델의 ‘시각적 특징’ 일반화 능력을 FAS에 활용

![image.png](attachment:c24b867a-b563-443f-8cfc-cceb765e377c:image.png)

### 4.2. FLIP-Image-Text Similarity (FLIP-IT)

- **Language Guidance** 도입
- **핵심 아이디어**: Image representation을 **Text prompt**의 semantic representation과 정렬하여 분류
- **작동 방식**
    - 입력 이미지 $I$ → ViT 인코더 $V$ → 이미지 임베딩 $x$
    - ‘Real’ 및 ‘Spoof’ 클래스를 설명하는 **텍스트 프롬프트** (e.g. “This is a real face”, “This is a spoof face”) → CLIP 텍스트 인코더 $L$ → 텍스트 임베딩 $z_r , z_s$
    - **Ensemble**: 클래스당 여러 프롬프트를 사용하여 텍스트 임베딩의 평균($\bar{z}$)을 사용 → Robust Representation Learning
    - 이미지 임베딩 $x$와 텍스트 임베딩 $\bar{z}$ 간의 **Cosine similarity**를 계산하여 Logits으로 사용
    - Softmax 함수를 통해 확률 계산
        
        $$
         p(\hat{y}|x) = \frac{\exp(\text{sim}(x, \bar{z}_{\hat{y}})/\tau)}{\exp(\text{sim}(x, \bar{z}_r)/\tau) + \exp(\text{sim}(x, \bar{z}_s)/\tau)} 
        $$
        

![image.png](attachment:020df3ff-1f5d-4928-b537-a698c87d6287:image.png)

- 이점
    - **의미론적 ‘안내(Grounding / Guidance)’**: 위조 공격의 미세한 특징(e.g.: 종이 질감, 화면 왜곡)을 텍스트 설명이라는 명확한 의미 기준에 연결
    - **도메인 간극 완화**: 텍스트는 이미지보다 도메인 변화에 덜 민감할 수 있으며, 이미지 특징을 텍스트 의미에 맞추면 일반화 성능 향상

### 4.3. FLIP-Multimodal-Contrastive-Learning (FLIP-MCL)

![image.png](attachment:95c52163-6c31-4b39-948c-c242ef86d693:image.png)

- **핵심 아이디어**: FLIP-IT에 **Self-Supervised Learning** 및 **Image-Text Similarity Consistency**을 추가하여 임베딩의 Robustness와 Domain-invariance 강화
- **전체 손실 함수**
    
    $$
     L_{mcl} = \alpha L_{ce} + \beta L_{simCLR} + \gamma L_{mse} 
    $$
    
    - **$L_{simCLR}$ (Image-based Contrastive Loss)**
        - 동일 이미지 $I$에 서로 다른 변환(view) $I_{v1}, I_{v2}$을 적용
        - 각 view의 features $x_{v1}, x_{v2}$를  non-linear projection network $H$를 통해 $h_{v1}, h_{v2}$로 변환
        - $h_{v1}, h_{v2}$ 간의 Contrastive learning으로 유사성 최대화
            
            ![image.png](attachment:00ac65ce-dea6-4e7e-922f-3bfe50237c8c:image.png)
            
    - **$L_{mse}$ (Image-Text View Consistency Loss)**
        - 두 개의 다른 Image view$(x_{v1}, x_{v2})$와 두 개의 다른 Text prompt view$(z_{v1}, z_{v2})$를 사용
        - 두 이미지-텍스트 쌍에서 계산된 Cosine similarity 점수( $sim(x_{v1}, z_{v1})$과 $sim(x_{v2}, z_{v2})$) 간의 **평균 제곱 오차(MSE)** 최소화
        - 목적: 이미지-텍스트 뷰 쌍의 일관성을 강제. 도메인 간극 완화에 기여
            
            ![image.png](attachment:7ae0ae70-6e12-4541-92ce-204f01cf04ab:image.png)
            

## 5. Experiment Setup

- **Datasets & DG Protocols**
    - **Protocol 1**: MSU-MFSD(M), CASIA-MFSD(C), Replay Attack(I), OULU-NPU(O)
    - **Protocol 2**: WMCA(W), CASIA-CeFA(C), CASIA-SURF(S)
    - **Protocol 3**: 12개 Single-source to Single-target 시나리오
    - CelebA-Spoof: 보조 훈련 데이터
- **Evaluation Metrics**
    - Half Total Error Rate (HTER) $\downarrow$
    - Area Under ROC Curve (AUC) $\uparrow$
    - True Positive Rate at Fixed False Positive Rate (TPR@FPR=1%) $\uparrow$
- **비교 대상**
    - SOTA Domain Generalization 방법
    - ViT 기반 FAS
    - **Zero-shot vs Five-shot**: 제안된 방법의 0-shot 성능으로 5-shot SOTA를 능가함을 강조
- **Implementation**
    - Image size: 224 x 224 x 3
    - Patch size: 16 x 16
    - Optimizer: Adam, Learning Rate: $10^{-6}$, Weight decay: $10^{-6}$
    - CLIP ViT base 사용
    - two-layer MLP head
    - Image representation $d_v=768$
    - Vision-Language embedding dim $d_{vl}=512$

## 6. Results

- Average HTER
- **Protocol 1**
    
    ![image.png](attachment:676304dd-cfa0-4dec-8e34-27e44c7d9167:image.png)
    
    - SOTA 0-shot ViT: 6.00%
    - 5-shot ViTAF: 3.31%
    - FLIP-V: 3.48%
    - FLIP-IT: 3.06%
    - FLIP-MCL: 3.01%
- **Protocol 2**
    
    ![image.png](attachment:4ff03ac8-fc20-43b9-b704-32e3c8b4c4e6:image.png)
    
- **Protocol 3: Challenging Single-Source to Target**
    
    ![image.png](attachment:5043d127-5d8b-4e31-9133-6546dc529866:image.png)
    
- **정리**
    - FLIP-V 만으로도 FAS 성능이 향상됨
    - FLIP-IT에서 Language guidance로 성능 추가 향상
    - FLIP-MCL, Multimodal contrastive learning으로 SOTA 성능 달성, 일부 지표에서는 0-shot 성능이 5-shot 성능을 능가함

## 7. Ablation Studies

- **Comparing ViT initialization methods for FAS**
    
    ![image.png](attachment:31954053-f219-43b5-969e-ce35476c5e12:image.png)
    
- **Impact of different text prompts**
    
    ![image.png](attachment:a3ea21e7-0a0e-4200-84f4-b457a1a6d792:image.png)
    
    ![image.png](attachment:7d772835-bbc2-4127-b71f-58de3f98bbf9:image.png)
    
- **Contribution of different loss terms**
    
    ![image.png](attachment:bee8bb4e-bf0b-4a9b-afc9-8711a9f02deb:image.png)
    

## 8. Visualization

- Attention Maps (Spoof Images)
    
    ![image.png](attachment:b2668750-73c4-48f1-8015-353df3513daf:image.png)
    
    ![image.png](attachment:7fd5b172-caf1-448f-a3ef-0c3908c339d1:image.png)
    
    - 모델이 위조 특징(e.g. 종이 질감, 테두리, 모아레 패턴, 옷 주름, 화면 가장자리)을 효과적으로 감지하고 있음을 보여줌
- Mis-classified Examples
    
    ![image.png](attachment:0c4d51d0-45d6-4b6d-adbc-b008239fd823:image.png)
    
    ![image.png](attachment:e9a395f6-451d-4028-9ce7-17dbd709d2ce:image.png)
    
    - **Real → Spoof**: 낮은 해상도, 조명 변화, 배경 텍스처 등 실제 얼굴 특징이 위조처럼 오인되는 경우
    - **Spoof → Real**: 고해상도 위조 샘플, 실제와 구분하기 어려운 정교한 위조 공격
    - 일부 어려운 케이스가 존재하지만 전반적으로 모델이 복잡한 도메인 변화에도 잘 대처하고 있음
        - OCI → M, no false positive cases
        - For OCM → I, 실제 샘플의 0.62%만 잘못 분류됨을 관찰
        - For ICM → O, 실제 샘플의 0.2%가 Spoofing으로 오분류

## 9. Conclusion

- **강점**
    - 탁월한 Cross-Domain generalize performance
    - VLP 모델 활용하여 간결한 접근 방식
    - Text prompt의 효과적 활용
    - 견고성 강화: Multimodal contrastive learning으로 다양한 환경에 대한 Robustness 확보
- **한계점**
    - 계산 비용 증가: Text encoder의 활용으로 학습 및 추론 시 추가적인 연산 필요
    - VLP 모델 의존성: CLIP 모델의 품질 및 일반화 성능에 따라 FAS 성능이 결정됨
    - 효과적인 프롬프트 구성을 위한 Domain/Attack 특성에 대한 이해 필요
- **결론**
    - VLP 모델(CLIP)을 FAS에 직접 적용하는 것은 매우 효과적이며, 특히 Language-guidance와 multimodal contrastive learning을 결합한 FLIP 프레임워크는 SOTA Cross-domain generalization performance를 달성함
    - 시각적 특징을 언어적 의미와 결합하여 FAS의 복잡한 문제를 해결할 잠재력이 있음을 보여줌
- **향후 연구 방향**
    - **다른 VLP 모델 탐색**: BERT, ALIGN, BLIP 등 다양한 VLP 모델로 일반화 가능성 검증
    - **Prompt Learning**: 고정된 프롬프트 대신 학습 가능한 프롬프트나 dynamic 프롬프트 생성 방식 연구
    - **효율성 개선**: Text Encoder의 연산 부담을 줄이기 위한 경량화, Knowledge distillation 등의 연구
    - 실시간 추론 속도 향상 및 다양한 실제 환경 데이터셋에서의 검증
