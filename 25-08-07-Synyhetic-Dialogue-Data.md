# Advancing Speech Language Models by Scaling Supervised Fine‑Tuning with Over 60,000 Hours of Synthetic Speech Dialogue Data
Date: 2025-08-08

**Keywords**: Speech-LLM, synthetic speech dialogues, Ke-SpeechChat, KE-Omni, large dataset, real-time interaction

**TL;DR**: Introduces a massive synthetic speech dialogue dataset (Ke-SpeechChat) and a real-time, bilingual speech language model (KE-Omni) with strong performance in both Chinese and English.

**Summary**:

- Created Ke‑SpeechChat, a synthetic dataset with 7 million dialogues (>60,000 hours), built from virtual speakers to ensure privacy, with high audio quality verified via DNSMOS and UTMOS metrics 


- Built KE‑Omni, a speech language model comprising a Whisper-based speech encoder, LLaMA‑3.1‑8B LLM, and a speech decoder with a unit-based vocoder, enabling seamless speech input and output 


- Evaluated on tasks including speech-to-text instruction-following, modality alignment, speech quality, and VoiceBench benchmarks. KE‑Omni notably outperforms previous models and improves with larger training subsets 


**Notes**: 
- Real-time interaction in two languages is impressive.
- Curious about the handling of environmental variability (like noise) and possibilities for multi-turn dialogues—both noted as limitations 
