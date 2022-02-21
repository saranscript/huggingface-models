---
language:
- ja  
license: apache-2.0
tags:
- audio
- automatic-speech-recognition
- speech
datasets:
- Japanese accent datasets
metrics:
- wer

# Optional. Add this if you want to encode your eval results in a structured way.
model-index:
- name: Wav2vec2 Accent Japanese
  results:
  - task: 
      type: Speech Recognition  # Required. Example: automatic-speech-recognition
      name: automatic-speech-recognition  # Optional. Example: Speech Recognition
    dataset:
      type: accent_voice  
      name: Japanese accent datasets 
      args: ja         
    metrics:
      - type: wer   # Required. 
        value: 15.82   # Required.
        name: Test WER            
---
# Wav2Vec2 Accent Japanese
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Japanese accent dataset 
When using this model, make sure that your speech input is sampled at 16kHz.

## Test Result
WER: 15.82%  