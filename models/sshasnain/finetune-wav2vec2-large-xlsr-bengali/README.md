---
language: Bengali
datasets:
- custom
metrics:
- wer
tags:
- bn
- audio
- automatic-speech-recognition
- speech
license: apache-2.0
model-index:
- name: finetune-wav2vec2-large-xlsr-bengali
  results:
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: custom
      type: custom
      args: ben
    metrics:
    - name: Test WER
      type: wer
      value: 0.011
---
 # finetune-wav2vec2-large-xlsr-bengali
***
## Usage
***