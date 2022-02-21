---
language:
- tr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: xslr-commonvoice
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xslr-commonvoice

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3835
- Wer: 0.3450

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
- num_epochs: 15.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 0.92  | 100  | 3.5761          | 1.0    |
| No log        | 1.83  | 200  | 3.0512          | 0.9999 |
| No log        | 2.75  | 300  | 1.0185          | 0.8188 |
| No log        | 3.67  | 400  | 0.5936          | 0.6411 |
| 3.2139        | 4.59  | 500  | 0.4986          | 0.5267 |
| 3.2139        | 5.5   | 600  | 0.4327          | 0.4732 |
| 3.2139        | 6.42  | 700  | 0.4227          | 0.4462 |
| 3.2139        | 7.34  | 800  | 0.4213          | 0.4291 |
| 3.2139        | 8.26  | 900  | 0.4016          | 0.4033 |
| 0.22          | 9.17  | 1000 | 0.3987          | 0.3825 |
| 0.22          | 10.09 | 1100 | 0.4065          | 0.3867 |
| 0.22          | 11.01 | 1200 | 0.3929          | 0.3842 |
| 0.22          | 11.93 | 1300 | 0.3775          | 0.3687 |
| 0.22          | 12.84 | 1400 | 0.3891          | 0.3536 |
| 0.1005        | 13.76 | 1500 | 0.3850          | 0.3492 |
| 0.1005        | 14.68 | 1600 | 0.3823          | 0.3441 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.9.1+cu102
- Datasets 1.14.0
- Tokenizers 0.10.3
