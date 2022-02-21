---
language:
- cs
- hsb
- pl
- sk
- sl
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
- xlsr-fine-tuning-week
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-300m-west-slavic-cv8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: cs
    metrics:
       - name: Test WER
         type: wer
         value: 53.5
       - name: Test CER
         type: cer 
         value: 14.7
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: hsb
    metrics:
       - name: Test WER
         type: wer
         value: 81.7
       - name: Test CER
         type: cer 
         value: 21.2
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: pl
    metrics:
       - name: Test WER
         type: wer
         value: 60.2
       - name: Test CER
         type: cer 
         value: 15.6
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sk
    metrics:
       - name: Test WER
         type: wer
         value: 69.6
       - name: Test CER
         type: cer 
         value: 20.7
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sl
    metrics:
       - name: Test WER
         type: wer
         value: 73.2
       - name: Test CER
         type: cer 
         value: 23.2
---

# wav2vec2-xls-r-300m-west-slavic-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the Common Voice 8 dataset of five similar languages with similar scripts: Czech, Slovak, Polish, Slovenian and Upper Sorbian. Training and validation sets were concatenated and shuffled.

Evaluation set used for training was concatenated from the respective test sets and shuffled while limiting each language to at most 2000 samples. During training, cca WER 70 was achieved on this set.

### Evaluation script

```
python eval.py --model_id comodoro/wav2vec2-xls-r-300m-west-slavic-cv8 --dataset mozilla-foundation/common_voice_8_0 --split test --config {lang}
```
                                                   
### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50
- mixed_precision_training: Native AMP

### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
