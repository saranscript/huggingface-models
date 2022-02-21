---
language: 
- sv-SE

license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
metrics:
- wer
- cer
model-index:
- name: wav2vec2-xls-r-300m-swedish
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice sv-SE # Required. Example: Common Voice zh-CN
      args: sv-SE       # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 24.73  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
        args: 
        - learning_rate: 7.5e-05
        - train_batch_size: 64
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 2
        - total_train_batch_size: 128
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 1000
        - num_epochs: 50
        - mixed_precision_training: Native AMP       # Optional. Example for BLEU: max_order
      - type: cer    # Required. Example: wer
        value: 7.58  # Required. Example: 20.90
        name: Test CER    # Optional. Example: Test WER
        args: 
        - learning_rate: 7.5e-05
        - train_batch_size: 64
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 2
        - total_train_batch_size: 128
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 1000
        - num_epochs: 50
        - mixed_precision_training: Native AMP        # Optional. Example for BLEU: max_order

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-Swedish

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3641
- Wer: 0.2473
- Cer: 0.0758


## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 64
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 6.1097        | 5.49  | 500  | 3.1422          | 1.0    | 1.0    |
| 2.985         | 10.98 | 1000 | 1.7357          | 0.9876 | 0.4125 |
| 1.0363        | 16.48 | 1500 | 0.4773          | 0.3510 | 0.1047 |
| 0.6111        | 21.97 | 2000 | 0.3937          | 0.2998 | 0.0910 |
| 0.4942        | 27.47 | 2500 | 0.3779          | 0.2776 | 0.0844 |
| 0.4421        | 32.96 | 3000 | 0.3745          | 0.2630 | 0.0807 |
| 0.4018        | 38.46 | 3500 | 0.3685          | 0.2553 | 0.0781 |
| 0.3759        | 43.95 | 4000 | 0.3618          | 0.2488 | 0.0761 |
| 0.3646        | 49.45 | 4500 | 0.3641          | 0.2473 | 0.0758 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
