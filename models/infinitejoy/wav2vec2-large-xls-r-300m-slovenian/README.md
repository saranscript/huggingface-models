---
language:
- sl
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- sl
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Slovenian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: sl
    metrics:
       - name: Test WER
         type: wer
         value: 18.970
       - name: Test CER
         type: cer
         value: 4.534
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: sl
    metrics:
       - name: Test WER
         type: wer
         value: 55.048
       - name: Test CER
         type: cer
         value: 22.739
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-slovenian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - SL dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2093
- Wer: 0.1907

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7e-05
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.785         | 12.5  | 1000 | 0.7465          | 0.6812 |
| 0.8989        | 25.0  | 2000 | 0.2495          | 0.2732 |
| 0.7118        | 37.5  | 3000 | 0.2126          | 0.2284 |
| 0.6367        | 50.0  | 4000 | 0.2049          | 0.2049 |
| 0.5763        | 62.5  | 5000 | 0.2116          | 0.2055 |
| 0.5196        | 75.0  | 6000 | 0.2111          | 0.1910 |
| 0.4949        | 87.5  | 7000 | 0.2131          | 0.1931 |
| 0.4797        | 100.0 | 8000 | 0.2093          | 0.1907 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
