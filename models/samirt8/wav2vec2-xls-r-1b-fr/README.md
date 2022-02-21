---
language:
- fr
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- fr
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-1B - French
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: fr
    metrics:
       - name: Test WER (without LM)
         type: wer
         value: 15.405483405483406
       - name: Test CER (without LM)
         type: cer
         value: 4.8773030225289137
       - name: Test WER (with LM)
         type: wer
         value: 12.5
---
This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - FR dataset.
It achieves the following results on the evaluation set:

**Without LM**:
- Wer: 0.154
**With LM**:
- Wer: 0.125