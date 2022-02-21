---
language:
- de
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- de
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-1B - German
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: de
    metrics:
       - name: Test WER
         type: wer
         value: 11.37
       - name: Test CER
         type: cer
         value: 2.89
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: de
    metrics:
       - name: Dev WER
         type: wer
         value: 31.16
       - name: Dev CER
         type: cer
         value: 13.41
---

# XLS-R-1b-DE

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - DE dataset. (See `run.sh` for training parameters).