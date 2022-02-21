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
- name: wav2vec2-60-urdu
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_7_0 # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice ur  # Required. Example: Common Voice zh-CN
      args: ur         # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 59.1  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
        args: 
        - learning_rate: 0.0003
        - train_batch_size: 16
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 2
        - total_train_batch_size: 32
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 200
        - num_epochs: 50
        - mixed_precision_training: Native AMP         # Optional. Example for BLEU: max_order
      - type: cer    # Required. Example: wer
        value: 33.1  # Required. Example: 20.90
        name: Test CER    # Optional. Example: Test WER
        args: 
        - learning_rate: 0.0003
        - train_batch_size: 16
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 2
        - total_train_batch_size: 32
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 200
        - num_epochs: 50
        - mixed_precision_training: Native AMP         # Optional. Example for BLEU: max_order
---
# wav2vec2-large-xlsr-53-urdu

This model is a fine-tuned version of [Harveenchadha/vakyansh-wav2vec2-urdu-urm-60](https://huggingface.co/Harveenchadha/vakyansh-wav2vec2-urdu-urm-60) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Wer: 0.5913
- Cer: 0.3310

## Model description
The training and valid dataset is 0.58 hours. It was hard to train any model on lower number of so I decided to take vakyansh-wav2vec2-urdu-urm-60 checkpoint and finetune the wav2vec2 model.  

## Training procedure
Trained on Harveenchadha/vakyansh-wav2vec2-urdu-urm-60 due to lesser number of samples.


### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
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
| 12.6045       | 8.33  | 100  | 8.4997          | 0.6978 | 0.3923 |
| 1.3367        | 16.67 | 200  | 5.0015          | 0.6515 | 0.3556 |
| 0.5344        | 25.0  | 300  | 9.3687          | 0.6393 | 0.3625 |
| 0.2922        | 33.33 | 400  | 9.2381          | 0.6236 | 0.3432 |
| 0.1867        | 41.67 | 500  | 6.2150          | 0.6035 | 0.3448 |
| 0.1166        | 50.0  | 600  | 6.4496          | 0.5913 | 0.3310 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
