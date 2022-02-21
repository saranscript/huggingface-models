---
language: 
- ur

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
- name: wav2vec2-urdu-V8-Abid
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice ur  # Required. Example: Common Voice zh-CN
      args: ur         # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 44.63 # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
        args: 
        - learning_rate: 7.5e-05
        - train_batch_size: 16
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 2
        - total_train_batch_size: 32
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 200
        - num_epochs: 50
        - mixed_precision_training: Native AMPP       # Optional. Example for BLEU: max_order
      - type: cer    # Required. Example: wer
        value: 18.82  # Required. Example: 20.90
        name: Test CER    # Optional. Example: Test WER
        args: 
        - learning_rate: 7.5e-05
        - train_batch_size: 16
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 2
        - total_train_batch_size: 32
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 200
        - num_epochs: 50
        - mixed_precision_training: Native AMPP
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-60-Urdu-V8

This model is a fine-tuned version of [Harveenchadha/vakyansh-wav2vec2-urdu-urm-60](https://huggingface.co/Harveenchadha/vakyansh-wav2vec2-urdu-urm-60) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 11.4832
- Wer: 0.5729
- Cer: 0.3170


### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 200
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 19.671        | 8.33  | 100  | 7.7671          | 0.8795 | 0.4492 |
| 2.085         | 16.67 | 200  | 9.2759          | 0.6201 | 0.3320 |
| 0.6633        | 25.0  | 300  | 8.7025          | 0.5738 | 0.3104 |
| 0.388         | 33.33 | 400  | 10.2286         | 0.5852 | 0.3128 |
| 0.2822        | 41.67 | 500  | 11.1953         | 0.5738 | 0.3174 |
| 0.2293        | 50.0  | 600  | 11.4832         | 0.5729 | 0.3170 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
