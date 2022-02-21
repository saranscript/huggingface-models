---
language: fa
datasets:
- common_voice
tags:
- robust-speech-event
widget:
- example_title: Common Voice sample 2978
  src: https://huggingface.co/manifoldix/xlsr-fa-lm/resolve/main/sample2978.flac
- example_title: Common Voice sample 5168
  src: https://huggingface.co/manifoldix/xlsr-fa-lm/resolve/main/sample5168.flac
model-index:
- name: XLS-R-300m Wav2Vec2 Persian 
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice fa
      type: common_voice
      args: fa  
    metrics:
       - name: Test WER without LM
         type: wer
         value: 26%
       - name: Test WER with LM
         type: wer
         value: 23%
---

## XLSR-300m Persian
Fine-tuned on commom voice FA
