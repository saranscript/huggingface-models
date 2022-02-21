---
language: id
datasets:
- common_voice 
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Indonesian by cahya
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice id
      type: common_voice
      args: id
    metrics:
       - name: Test WER
         type: wer
         value: 25.86
---

Dummy Model New