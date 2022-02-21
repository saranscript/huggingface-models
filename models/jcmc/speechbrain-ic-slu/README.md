---
library_name: speechbrain
tags:
- audio
- intent classification 
datasets:
- fluent_speech_commands_dataset
metrics:
- wer 

model-index:
- name: Direct SLU
  results:
  - task: 
      type: automatic-speech-recognition
      name: Intent Classification
    metrics:
      - type: wer    # Required. Example: wer
        value: 7.0  # Required. Example: 20.90
        name: Test Wer
---

Speechbrain SLU fine-tuned for Intent Classification
---
Model: Direct SLU  
Encoder: Pre-trained ASR encoder -> LSTM  
Decoder: GRU + beamsearch  
Tokens: BPE with unigram  
Data: fluent_speech_commands_dataset (http://140.112.21.28:9000/fluent.tar.gz)  
Test wer: 0.07