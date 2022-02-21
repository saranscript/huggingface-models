---
tags:
- robust-speech-event
widget:
- example_title: swiss parliament sample 1
  src: https://huggingface.co/manifoldix/xlsr-sg-lm/resolve/main/07e73bcaa2ab192aea9524d72db45f34f274d1b3d5672434c462d32d44d792be.mp3
- example_title: swiss parliament sample 2
  src: https://huggingface.co/manifoldix/xlsr-sg-lm/resolve/main/14a2f855363920f111c7b30e8632c19e5f340ab5031e1ed2621db39baf452ae0.mp3
  
model-index:
- name: XLS-R-1b Wav2Vec2 Swiss German 
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    
    metrics:
       - name: Test WER on Swiss parliament
         type: wer
         value: 34.6%
       - name: Test WER on Swiss dialect test set
         type: wer
         value: 40%
---

## XLSR-1b Swiss German
Fine-tuned on the Swiss parliament dataset from FHNW v1 (70h).

Tested on the Swiss parliament test set with a WER of 34.6%

Tested on the "Swiss German Dialects" with a WER of 40%

Both test sets can be accessed here: [fhnw_datasets](https://www.cs.technik.fhnw.ch/i4ds-datasets)

The Swiss German dialect private test set has been uploaded on huggingface: [huggingface_swiss_dialects](https://huggingface.co/datasets/manifoldix/swg_parliament_fhnw)