---
language:
- mr
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-large-xls-r-300m-mr
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice 8
      args: mr
    metrics:
      - type: wer    # Required. Example: wer
        value: 49.70  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
      - name: Test CER
        type: cer
        value: 11.11
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - MR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5319
- Wer: 0.5973

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 200.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 3.3987        | 22.73  | 500  | 3.3586          | 1.0    |
| 2.0563        | 45.45  | 1000 | 1.0375          | 0.8428 |
| 1.283         | 68.18  | 1500 | 0.5563          | 0.6996 |
| 1.0308        | 90.91  | 2000 | 0.4922          | 0.6398 |
| 0.8803        | 113.64 | 2500 | 0.4949          | 0.6153 |
| 0.7581        | 136.36 | 3000 | 0.4932          | 0.5965 |
| 0.6681        | 159.09 | 3500 | 0.5133          | 0.5921 |
| 0.6191        | 181.82 | 4000 | 0.5281          | 0.5909 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu113
- Datasets 1.18.3.dev0
- Tokenizers 0.11.0
