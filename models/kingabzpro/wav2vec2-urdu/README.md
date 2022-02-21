---
language: 
- ur

license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
metrics:
- wer
- cer
model-index:
- name: wav2vec2-urdu
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_7_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice ur  # Required. Example: Common Voice zh-CN
      args: ur         # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 52.40 # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
        args: 
        - learning_rate: 0.0003
        - train_batch_size: 64
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 2
        - total_train_batch_size: 128
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 100
        - num_epochs: 100
        - mixed_precision_training: Native AMP        # Optional. Example for BLEU: max_order
      - type: cer    # Required. Example: wer
        value: 26.46  # Required. Example: 20.90
        name: Test CER  # Optional. Example: Test WER
        args: 
        - learning_rate: 0.0003
        - train_batch_size: 64
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 2
        - total_train_batch_size: 128
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 100
        - num_epochs: 100
        - mixed_precision_training: Native AMP
      - type: wer   # Required. Example: wer
        value: 45.63  # Required. Example: 20.90
        name: Test WER LM CV8     # Optional. Example: Test WER
      - type: cer # Required. Example: wer
        value: 20.45  # Required. Example: 20.90
        name: Test CER LM CV8    # Optional. Example: Test WER  
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-Urdu

This model is a fine-tuned version of [Harveenchadha/vakyansh-wav2vec2-urdu-urm-60](https://huggingface.co/Harveenchadha/vakyansh-wav2vec2-urdu-urm-60) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Wer: 0.5747
- Cer: 0.3268

## Model description
The training and valid dataset is 0.58 hours. It was hard to train any model on lower number of so I decided to take vakyansh-wav2vec2-urdu-urm-60 checkpoint and finetune the wav2vec2 model.  

## Training procedure
Trained on Harveenchadha/vakyansh-wav2vec2-urdu-urm-60 due to lesser number of samples.

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 64
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 4.3054        | 16.67 | 50   | 9.0055          | 0.8306 | 0.4869 |
| 2.0629        | 33.33 | 100  | 9.5849          | 0.6061 | 0.3414 |
| 0.8966        | 50.0  | 150  | 4.8686          | 0.6052 | 0.3426 |
| 0.4197        | 66.67 | 200  | 12.3261         | 0.5817 | 0.3370 |
| 0.294         | 83.33 | 250  | 11.9653         | 0.5712 | 0.3328 |
| 0.2329        | 100.0 | 300  | 7.6846          | 0.5747 | 0.3268 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
