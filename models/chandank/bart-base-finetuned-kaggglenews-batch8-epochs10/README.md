---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: bart-base-finetuned-kaggglenews-batch8-epochs10
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-base-finetuned-kaggglenews-batch8-epochs10

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5763
- Rouge1: 28.693
- Rouge2: 16.666
- Rougel: 24.2361
- Rougelsum: 26.0289
- Gen Len: 20.0

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| No log        | 1.0   | 495  | 1.6043          | 27.8611 | 15.8713 | 23.8365 | 25.378    | 20.0    |
| 1.9054        | 2.0   | 990  | 1.5613          | 28.2715 | 16.3724 | 24.3212 | 25.8499   | 20.0    |
| 1.651         | 3.0   | 1485 | 1.5394          | 28.6282 | 16.2976 | 24.2336 | 25.9434   | 20.0    |
| 1.4955        | 4.0   | 1980 | 1.5438          | 28.9266 | 16.7257 | 24.61   | 26.443    | 20.0    |
| 1.4034        | 5.0   | 2475 | 1.5449          | 28.2296 | 16.1292 | 23.9698 | 25.651    | 20.0    |
| 1.3077        | 6.0   | 2970 | 1.5642          | 28.4486 | 16.3833 | 24.1629 | 26.0013   | 20.0    |
| 1.2505        | 7.0   | 3465 | 1.5566          | 28.5469 | 16.5374 | 24.2966 | 25.962    | 20.0    |
| 1.2027        | 8.0   | 3960 | 1.5730          | 28.7278 | 16.6442 | 24.2531 | 26.1171   | 20.0    |
| 1.1571        | 9.0   | 4455 | 1.5690          | 28.7736 | 16.7491 | 24.3066 | 26.1439   | 20.0    |
| 1.1237        | 10.0  | 4950 | 1.5763          | 28.693  | 16.666  | 24.2361 | 26.0289   | 20.0    |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
