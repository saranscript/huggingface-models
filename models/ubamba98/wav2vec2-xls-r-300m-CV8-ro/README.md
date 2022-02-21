---
language:
- ro
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-300m-CV8-ro
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-CV8-ro

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - RO dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1578
- Wer: 0.6040
- Cer: 0.0475

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
- gradient_accumulation_steps: 4
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 2.9736        | 3.62  | 500  | 2.9508          | 1.0    | 1.0    |
| 1.3293        | 7.25  | 1000 | 0.3330          | 0.8407 | 0.0862 |
| 0.956         | 10.87 | 1500 | 0.2042          | 0.6872 | 0.0602 |
| 0.9509        | 14.49 | 2000 | 0.2184          | 0.7088 | 0.0652 |
| 0.9272        | 18.12 | 2500 | 0.2312          | 0.7211 | 0.0703 |
| 0.8561        | 21.74 | 3000 | 0.2158          | 0.6838 | 0.0631 |
| 0.8258        | 25.36 | 3500 | 0.1970          | 0.6844 | 0.0601 |
| 0.7993        | 28.98 | 4000 | 0.1895          | 0.6698 | 0.0577 |
| 0.7525        | 32.61 | 4500 | 0.1845          | 0.6453 | 0.0550 |
| 0.7211        | 36.23 | 5000 | 0.1781          | 0.6274 | 0.0531 |
| 0.677         | 39.85 | 5500 | 0.1732          | 0.6188 | 0.0514 |
| 0.6517        | 43.48 | 6000 | 0.1691          | 0.6177 | 0.0503 |
| 0.6326        | 47.1  | 6500 | 0.1619          | 0.6045 | 0.0479 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
