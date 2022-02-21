---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bart-finetuned-pubmed
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-finetuned-pubmed

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5363
- Rouge2 Precision: 0.3459
- Rouge2 Recall: 0.2455
- Rouge2 Fmeasure: 0.2731

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
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge2 Precision | Rouge2 Recall | Rouge2 Fmeasure |
|:-------------:|:-----:|:-----:|:---------------:|:----------------:|:-------------:|:---------------:|
| 1.652         | 1.0   | 1125  | 1.5087          | 0.3647           | 0.2425        | 0.2772          |
| 1.4695        | 2.0   | 2250  | 1.5039          | 0.3448           | 0.2457        | 0.2732          |
| 1.3714        | 3.0   | 3375  | 1.4842          | 0.3509           | 0.2474        | 0.277           |
| 1.2734        | 4.0   | 4500  | 1.4901          | 0.3452           | 0.2426        | 0.2716          |
| 1.1853        | 5.0   | 5625  | 1.5152          | 0.3658           | 0.2371        | 0.2744          |
| 1.0975        | 6.0   | 6750  | 1.5133          | 0.3529           | 0.2417        | 0.2729          |
| 1.0448        | 7.0   | 7875  | 1.5203          | 0.3485           | 0.2464        | 0.275           |
| 0.9999        | 8.0   | 9000  | 1.5316          | 0.3437           | 0.2435        | 0.2719          |
| 0.9732        | 9.0   | 10125 | 1.5338          | 0.3464           | 0.2446        | 0.2732          |
| 0.954         | 10.0  | 11250 | 1.5363          | 0.3459           | 0.2455        | 0.2731          |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
