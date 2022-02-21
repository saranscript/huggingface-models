---
language:
- pt
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- pt
license: apache-2.0
model-index:
- name: bp_400h_xlsr2_300M
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: pt
    metrics:
       - name: Test WER
         type: wer
         value: 10.83
       - name: Test CER
         type: cer
         value: 3.11
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: sv
    metrics:
       - name: Test WER
         type: wer
         value: 22.48
       - name: Test CER
         type: cer
         value: 9.33
---

# bp_400h_xlsr2_300M