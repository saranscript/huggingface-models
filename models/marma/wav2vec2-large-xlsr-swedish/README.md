---
language: sv
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Swedish by Marma
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice sv-SE
      type: common_voice
      args: sv  
    metrics:
       - name: Test WER
         type: wer
         value: 23.33
---

# Wav2Vec2-Large-XLSR-53-Swedish

This model has moved [here](https://huggingface.co/KBLab/wav2vec2-large-xlsr-53-swedish)