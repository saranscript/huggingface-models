---
license: apache-2.0
tags:
- audio-classification
- generated_from_trainer
datasets:
- common_language
metrics:
- accuracy
model-index:
- name: distilhubert-ft-common-language
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilhubert-ft-common-language

This model is a fine-tuned version of [ntu-spml/distilhubert](https://huggingface.co/ntu-spml/distilhubert) on the common_language dataset.
It achieves the following results on the evaluation set:
- Loss: 2.7214
- Accuracy: 0.2797

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 32
- eval_batch_size: 4
- seed: 0
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 3.6543        | 1.0   | 173  | 3.7611          | 0.0491   |
| 3.2221        | 2.0   | 346  | 3.4868          | 0.1352   |
| 2.9332        | 3.0   | 519  | 3.2732          | 0.1861   |
| 2.7299        | 4.0   | 692  | 3.0944          | 0.2172   |
| 2.5638        | 5.0   | 865  | 2.9790          | 0.2400   |
| 2.3871        | 6.0   | 1038 | 2.8668          | 0.2590   |
| 2.3384        | 7.0   | 1211 | 2.7972          | 0.2653   |
| 2.2648        | 8.0   | 1384 | 2.7625          | 0.2695   |
| 2.2162        | 9.0   | 1557 | 2.7405          | 0.2782   |
| 2.1915        | 10.0  | 1730 | 2.7214          | 0.2797   |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
