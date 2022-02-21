---
language:
- en  

license: Academic Free License v3.0  

tags:
- audio  # Example: audio
- automatic-speech-recognition  # Example: automatic-speech-recognition
- speech  # Example: speech

pipeline_tag: automatic-speech-recognition

datasets:
- timit_asr # Example: common_voice. Use dataset id from https://hf.co/datasets

metrics:
- wer  

# Optional. Add this if you want to encode your eval results in a structured way.
model-index:
- name: iloko-model
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Iloko Speech Recognition  # Optional. Example: Speech Recognition
   
    metrics:
      - type: wer   # Required. Example: wer
        value: 0.009 # Required. Example: 20.90
        name: TEST WETR    # Optional. Example: Test WER
       # args: {arg_0}          # Optional. Example for BLEU: max_order
---
FINETUNED ILOKANO SPEECH RECOGNITION FROM WAV2VEC-XLSR-S3