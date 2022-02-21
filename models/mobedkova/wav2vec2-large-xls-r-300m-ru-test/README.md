---
language:
- ru
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- common_voice
model-index:
- name: Russian Wav2Vec2 XLS-R 300m
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice-7.0
      type: mozilla-foundation/common_voice_7_0
      args: ru
    metrics:
       - name: Test WER
         type: wer
         value: 27.81
       - name: Test CER
         type: cer
         value: 8.83
---

# Russian Speech Recognition model