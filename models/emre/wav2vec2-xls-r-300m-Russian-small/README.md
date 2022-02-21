---
license: apache-2.0
language:
- ru
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-Russian-small
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice ru
      type: common_voice
      args: ru
    metrics:
       - name: Test WER
         type: wer
         value: 48.38
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-Russian-small

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3514
- Wer: 0.4838

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

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
- lr_scheduler_warmup_steps: 500
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.512         | 1.32  | 400  | 3.2207          | 1.0    |
| 3.1562        | 2.65  | 800  | 3.0166          | 1.0    |
| 1.5211        | 3.97  | 1200 | 0.7134          | 0.8275 |
| 0.6724        | 5.3   | 1600 | 0.4713          | 0.6402 |
| 0.4693        | 6.62  | 2000 | 0.3904          | 0.5668 |
| 0.3693        | 7.95  | 2400 | 0.3609          | 0.5121 |
| 0.3004        | 9.27  | 2800 | 0.3514          | 0.4838 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
