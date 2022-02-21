---
language: Bengali
datasets:
- custom
metrics:
- wer
tags:
- bn
- audio
- automatic-speech-recognition
- speech
license: apache-2.0
model-index:
- name: wav2vec2-xls-r-300m-bangla-command
  results:
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: custom
      type: custom
      args: ben
    metrics:
    - name: Test WER
      type: wer
      value: 0.006
---
 # wav2vec2-xls-r-300m-bangla-command
***
## Usage
Commands
'৫ টা কলম দেন' 

'চেয়ারটা কোথায় রেখেছেন' 

'ডানের বালতিটার প্রাইজ কেমন'

'দশ কেজি আলু কত'

'বাজুসের ল্যাপটপটা এসেছে' 

'বাসার জন্য দরজা আছে' 

'ম্যাম মোবাইলটা কি আছে' 

'হ্যালো শ্যাম্পুর দাম বল'