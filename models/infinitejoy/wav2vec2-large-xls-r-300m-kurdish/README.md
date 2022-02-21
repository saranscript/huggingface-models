---
language:
- kmr
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- kmr
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Kurmanji Kurdish
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: kmr
    metrics:
       - name: Test WER
         type: wer
         value: 102.308
       - name: Test CER
         type: cer
         value: 538.748
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-kurdish

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - KMR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2548
- Wer: 0.2688

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
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.3161        | 12.27 | 2000  | 0.4199          | 0.4797 |
| 1.0643        | 24.54 | 4000  | 0.2982          | 0.3721 |
| 0.9718        | 36.81 | 6000  | 0.2762          | 0.3333 |
| 0.8772        | 49.08 | 8000  | 0.2586          | 0.3051 |
| 0.8236        | 61.35 | 10000 | 0.2575          | 0.2865 |
| 0.7745        | 73.62 | 12000 | 0.2603          | 0.2816 |
| 0.7297        | 85.89 | 14000 | 0.2539          | 0.2727 |
| 0.7079        | 98.16 | 16000 | 0.2554          | 0.2681 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
