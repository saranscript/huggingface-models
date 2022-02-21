---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-tune_0.00005_4
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-tune_0.00005_4

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5405
- Wer: 0.4744

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.4032        | 0.86  | 1000  | 2.1379          | 0.8193 |
| 1.4611        | 1.72  | 2000  | 1.4984          | 0.5155 |
| 1.315         | 2.59  | 3000  | 1.4401          | 0.4707 |
| 1.2574        | 3.45  | 4000  | 1.3587          | 0.4559 |
| 1.1924        | 4.31  | 5000  | 1.3372          | 0.4450 |
| 1.1313        | 5.17  | 6000  | 1.3187          | 0.4351 |
| 1.0911        | 6.03  | 7000  | 1.3446          | 0.4354 |
| 1.0753        | 6.9   | 8000  | 1.3450          | 0.4396 |
| 1.0504        | 7.76  | 9000  | 1.3342          | 0.4378 |
| 1.0249        | 8.62  | 10000 | 1.3442          | 0.4335 |
| 1.0327        | 9.48  | 11000 | 1.3412          | 0.4293 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
