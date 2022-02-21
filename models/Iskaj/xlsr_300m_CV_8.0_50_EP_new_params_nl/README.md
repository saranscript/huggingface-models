
---
language:
- nl
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- nl
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Dutch 
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8 NL
      type: mozilla-foundation/common_voice_8_0
      args: nl
    metrics:
       - name: Test WER
         type: wer
         value: 35.44
       - name: Test CER
         type: cer
         value: 19.57
---

# xlsr_300m_CV_8.0_50_EP_new_params_nl