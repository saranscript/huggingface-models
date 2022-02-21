---
tags:
- generated_from_trainer
model-index:
- name: roberta-twitter-spam-classifier
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-twitter-spam-classifier

This model is a fine-tuned version of [cardiffnlp/twitter-roberta-base](https://huggingface.co/cardiffnlp/twitter-roberta-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3856
- Micro-avg-precision: 0.8723
- Micro-avg-recall: 0.8490
- Micro-avg-f1-score: 0.8594

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
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Micro-avg-precision | Micro-avg-recall | Micro-avg-f1-score |
|:-------------:|:-----:|:-----:|:---------------:|:-------------------:|:----------------:|:------------------:|
| 0.4923        | 1.0   | 2762  | 0.5676          | 0.8231              | 0.6494           | 0.6676             |
| 0.535         | 2.0   | 5524  | 0.4460          | 0.8065              | 0.8215           | 0.8132             |
| 0.5492        | 3.0   | 8286  | 0.6005          | 0.6635              | 0.5843           | 0.3906             |
| 0.5947        | 4.0   | 11048 | 0.5710          | 0.7875              | 0.7799           | 0.7835             |
| 0.4976        | 5.0   | 13810 | 0.5194          | 0.8375              | 0.7544           | 0.7800             |
| 0.5263        | 6.0   | 16572 | 0.5491          | 0.8739              | 0.7159           | 0.7475             |
| 0.4701        | 7.0   | 19334 | 0.4609          | 0.8681              | 0.7786           | 0.8069             |
| 0.4566        | 8.0   | 22096 | 0.4100          | 0.8637              | 0.8281           | 0.8430             |
| 0.4339        | 9.0   | 24858 | 0.4395          | 0.8642              | 0.8454           | 0.8540             |
| 0.3906        | 10.0  | 27620 | 0.3856          | 0.8723              | 0.8490           | 0.8594             |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
