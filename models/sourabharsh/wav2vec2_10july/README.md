---
language: de
datasets:
- common_voice
metrics:
- wer
- cer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 German by Jonatas Grosman
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice de
      type: common_voice
      args: de
    metrics:
       - name: Test WER
         type: wer
         value: 10.55
       - name: Test CER
         type: cer
         value: 2.81
---