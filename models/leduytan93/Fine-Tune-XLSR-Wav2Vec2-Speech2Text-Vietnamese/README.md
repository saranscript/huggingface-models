---
language: vi
datasets:
- common_voice
- FOSD: https://data.mendeley.com/datasets/k9sxg2twv4/4
metrics:
- wer
tags:
- language-modeling
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: MT5 Fix Asr Vietnamese by Ontocord
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice vi
      type: common_voice
      args: vi
    metrics:
       - name: Test WER
         type: wer
         value: 25.207182
---
