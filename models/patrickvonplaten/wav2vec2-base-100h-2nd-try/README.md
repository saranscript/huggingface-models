---
language: en
datasets:
- librispeech_asr
tags:
- audio
- automatic-speech-recognition
license: apache-2.0
widget:
- example_title: IEMOCAP sample 1
  src: https://cdn-media.huggingface.co/speech_samples/IEMOCAP_Ses01F_impro03_F013.wav
- example_title: IEMOCAP sample 2
  src: https://cdn-media.huggingface.co/speech_samples/IEMOCAP_Ses01F_impro04_F000.wav
- example_title: LibriSpeech sample 1
  src: https://cdn-media.huggingface.co/speech_samples/LibriSpeech_61-70968-0000.flac
- example_title: LibriSpeech sample 2
  src: https://cdn-media.huggingface.co/speech_samples/LibriSpeech_61-70968-0001.flac
- example_title: VoxCeleb sample 1
  src: https://cdn-media.huggingface.co/speech_samples/VoxCeleb1_00003.wav
- example_title: VoxCeleb sample 2
  src: https://cdn-media.huggingface.co/speech_samples/VoxCeleb_00004.wav
---

Second fine-tuning try of `wav2vec2-base`. Results are similar to the ones reported in https://huggingface.co/facebook/wav2vec2-base-100h.

Model was trained on *librispeech-clean-train.100* with following hyper-parameters:

- 2 GPUs Titan RTX
- Total update steps 11000
- Batch size per GPU: 32 corresponding to a *total batch size* of ca. ~750 seconds
- Adam with linear decaying learning rate with 3000 warmup steps
- dynamic padding for batch
- fp16
- attention_mask was **not** used during training

Check: https://wandb.ai/patrickvonplaten/huggingface/runs/1yrpescx?workspace=user-patrickvonplaten

*Result (WER)* on Librispeech:

| "clean" (% rel difference to results in paper) | "other" (% rel difference to results in paper) |
|---|---|
| 6.2 (-1.6%) | 15.2 (-11.2%)|