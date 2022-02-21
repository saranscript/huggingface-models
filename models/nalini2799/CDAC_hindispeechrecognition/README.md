---
language: hi
datasets:
- Interspeech 2021
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Hindi by Nalini Kumari
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice hi
      type: common_voice
      args: hi  
    metrics:
       - name: Test WER
         type: wer
         value: 72.73
---

# Hindi-Speech to Text Model </br>
The primary objective of this project is to develop a speech recognition system for the Hindi language. As there are very few systems available for speech to text in the Hindi language. Therefore it is an attempt to develop a system where a language model is developed using Machine learning libraries for speech-to-text conversion in the Hindi language. 