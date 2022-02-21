---
language: "ar"
pipeline_tag: automatic-speech-recognition
tags:
- CTC
- Attention
- pytorch
- speechbrain
- Transformer
license: "cc-by-nc-4.0"
datasets:
- commonvoice
metrics:
- wer
- cer
model-index:
- name: asafaya/hubert-large-arabic-ft
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice ar
      type: common_voice
      args: ar
    metrics:
       - name: Test WER
         type: wer
         value: 17.68
       - name: Test CER
         type: cer
         value: 5.49
       - name: Validation WER
         type: wer
         value: 10.93
       - name: Validation CER
         type: cer
         value: 3.13
---

# Arabic Hubert-Large - with CTC fine-tuned on Common Voice 8.0 (No LM)

This model is a fine-tuned version of [Arabic Hubert-Large](https://huggingface.co/asafaya/hubert-large-arabic). We finetuned this model on the Arabic CommonVoice dataset, acheiving a state of the art for commonvoice arabic test set WER of `17.68%` and CER of `5.49%`. 

The original model was pre-trained on 2,000 hours of 16kHz sampled Arabic speech audio. When using the model make sure that your speech input is also sampled at 16Khz, see the original [paper](https://arxiv.org/abs/2106.07447) for more details on the model.

The performance of the model on CommonVoice Arabic 8.0 is the following:

| Valid WER | Valid CER | Test WER | Test CER |
|:---------:|:---------:|:--------:|:--------:|
|   10.93   |   3.13    |  17.68   |   5.49   |

This model is trained using [SpeechBrain](https://speechbrain.github.io). 

# Usage

You can try the model using SpeechBrain as follows:

Install SpeechBrain and Transformers:

```
pip install speechbrain transformers
```

Then run the following code:

```python
from speechbrain.pretrained import EncoderASR

asr_model = EncoderASR.from_hparams(source="asafaya/hubert-large-arabic-ft", savedir="pretrained_models/asafaya/hubert-large-arabic-ft")

print(asr_model.transcribe_file("pretrained_models/asafaya/hubert-large-arabic-ft/example.wav"))

> وصلوا واحدا خلف الآخر 
```

More about [SpeechBrain](https://speechbrain.github.io).

# License

This work is licensed under [CC BY-NC-4.0](https://creativecommons.org/licenses/by-nc/4.0/legalcode).

# Citation


# Acknowledgement

Model fine-tuning and data processing for in this work were performed at [KUACC](ai.ku.edu.tr/) Cluster.
