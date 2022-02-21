---
language: fr
datasets:
- common_voice
tags:
- audio
- automatic-speech-recognition
- speech
- BPE
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: wav2vec2-large-xlsr-53-French-BPE by Ilyes Rebai
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice fr
      type: common_voice
      args: fr
    metrics:
       - name: Test WER
         type: wer
         value: 17.32
       - name: Test CER
         type: cer
         value: 7.03
---

The script used for training can be found here: https://github.com/irebai/wav2vec2

## Results

WER=17.32%

CER=7.03%
