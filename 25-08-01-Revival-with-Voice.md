# Revival with Voice: Multi-modal Controllable Text-to-Speech Synthesis
Date: 2025-08-01

## Keywords
- Multi-modal Controllable Text-to-Speech Synthesis- Face-driven TTS
- Speech Characteristics Control
- Speech Quality Improvement)
- Style Augmentation
- Consistent Voice Generation

## TL;DR
얼굴 이미지로부터 음성을 생성하고 자연어 텍스트 설명을 통해 발화 특성(예: 속도, 노이즈 수준, 톤)을 제어할 수 있는 MultiModal TTS 모델인 RV-TTS를 제안

## Summary
### Movitavtion
배경: 얼굴 이미지 기반 TTS는 음성 샘플 없이도 개인화된 음성을 생성할 수 있어 유용하지만, 다음과 같은 한계가 존재함:

오디오-비주얼 코퍼스의 품질 저하 (잡음, 말더듬 등)

예술적 초상화와 같은 비정형 얼굴 이미지에 대한 일반화 부족

얼굴-음성 간 매핑의 불확실성 (다대다 가능성)에도 불구하고 단일 출력만 생성하려는 기존 방법의 한계

목표: 이러한 한계를 해결하고, 얼굴 이미지 + 자연어 설명 기반의 다중 모달 제어형 TTS를 실현하는 것이 핵심 동기

### Method
RV-TTS (Revival with Voice): MusicGen 기반 스피치 언어 모델로, 다음과 같은 모듈 구성 및 학습 전략 사용함
- Input 
  - 텍스트 → 텍스트 임베딩 (T5 기반)
  - 얼굴 이미지 → face encoder (ResNet50)로 음성 임베딩 생성 
  - 자연어 설명 → 텍스트 임베딩 (T5)

- Output 
  - Transformer 기반 autoregressive 모델이 RVQ 코드를 예측 → 디코더를 통해 음성 재구성

Key Method:
- Face-Voice Contrastive Learning: 얼굴과 오디오 임베딩을 InfoNCE loss로 정렬 (ECAPA-TDNN 사용)
- Voice Embedding 교대 학습: 오디오 전용 / 오디오-비주얼 데이터셋을 번갈아 사용하며 TTS 모델에 face/audio-driven 임베딩을 조건으로 입력 
- Style Augmentation: 스타일 전이(CAST) 및 그레이스케일/블러링을 통해 예술적 초상화에 대한 일반화 능력 향상
- Sampling + Prompting 기반 In-Context Learning: 얼굴 하나에 다양한 음성을 생성하고, 원하는 샘플을 프롬프트로 재사용하여 일관된 음성 생성 가능

### Experiments and Results
- Dataset : LRS3, VoxCeleb2 (오디오-비주얼), LibriTTS-R (고품질 오디오 전용)
- Metrix : MOS (자연스러움), FMS (얼굴-음성 매칭), SIM (화자 유사성), VCS (음성 일관성), SNR, Speaking Rate 등
- Results 
  - Ablation 실험에서 LibriTTS-R와 스타일 증강이 핵심 성능 향상 요소임을 확인 
  - 기존 FaceTTS, YourTTS, FVTTS 대비 MOS, FMS, 화자 인식 정확도에서 큰 폭의 개선 
  - 자연어 설명을 통한 속도, 거리, 톤 등 음성 제어 능력 입증

### Contributions and Limitations
Contributions
- 고품질 오디오 통합과 멀티모달 임베딩 교대 학습을 통해 데이터 품질 격차 해소
- 스타일 증강을 통한 예술적 초상화 일반화 달성
- 샘플링-기반 in-context prompting으로 다양한/일관된 음성 생성 모두 달성
- 설명 텍스트 기반 제어를 통해 유연한 음성 스타일 제어 가능성 제시

Limitations
- 설명 텍스트 기반 제어는 미세 조정에 대한 명확한 기준 또는 제어 정확도에 대한 정량적 한계가 있음
- 음성의 일관성을 유지하기 위한 prompting 방식은 사용자 개입이 필요하며 자동화 측면에서 불완전할 수 있음
- 예술적 초상화 일반화는 일부 스타일에 대해 제한적일 수 있음 (style transfer의 품질에 의존)

