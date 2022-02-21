---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: t5-small-finetuned-pubmed
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-pubmed

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6131
- Rouge2 Precision: 0.3
- Rouge2 Recall: 0.2152
- Rouge2 Fmeasure: 0.2379

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge2 Precision | Rouge2 Recall | Rouge2 Fmeasure |
|:-------------:|:-----:|:----:|:---------------:|:----------------:|:-------------:|:---------------:|
| 2.1335        | 1.0   | 563  | 1.7632          | 0.2716           | 0.1936        | 0.2135          |
| 1.9373        | 2.0   | 1126 | 1.7037          | 0.2839           | 0.2068        | 0.2265          |
| 1.8827        | 3.0   | 1689 | 1.6723          | 0.2901           | 0.2118        | 0.2316          |
| 1.8257        | 4.0   | 2252 | 1.6503          | 0.2938           | 0.2115        | 0.2332          |
| 1.8152        | 5.0   | 2815 | 1.6386          | 0.2962           | 0.2139        | 0.2357          |
| 1.7939        | 6.0   | 3378 | 1.6284          | 0.2976           | 0.212         | 0.2354          |
| 1.7845        | 7.0   | 3941 | 1.6211          | 0.2991           | 0.2155        | 0.2383          |
| 1.7468        | 8.0   | 4504 | 1.6167          | 0.2994           | 0.217         | 0.239           |
| 1.7464        | 9.0   | 5067 | 1.6137          | 0.3007           | 0.2154        | 0.2382          |
| 1.744         | 10.0  | 5630 | 1.6131          | 0.3              | 0.2152        | 0.2379          |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
