---
tags:
- generated_from_trainer
datasets:
- null
model-index:
- name: BibliBERT
  results:
  - task:
      name: Masked Language Modeling
      type: fill-mask
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BibliBERT

This model is a fine-tuned version of [dbmdz/bert-base-italian-xxl-cased](https://huggingface.co/dbmdz/bert-base-italian-xxl-cased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7784

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
- seed: 0
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 50

### Training results

| Training Loss | Epoch | Step   | Validation Loss |
|:-------------:|:-----:|:------:|:---------------:|
| 1.5764        | 1.0   | 16528  | 1.5214          |
| 1.4572        | 2.0   | 33056  | 1.4201          |
| 1.3787        | 3.0   | 49584  | 1.3728          |
| 1.3451        | 4.0   | 66112  | 1.3245          |
| 1.3066        | 5.0   | 82640  | 1.2614          |
| 1.2447        | 6.0   | 99168  | 1.2333          |
| 1.2172        | 7.0   | 115696 | 1.2149          |
| 1.2079        | 8.0   | 132224 | 1.1853          |
| 1.2167        | 9.0   | 148752 | 1.1586          |
| 1.2056        | 10.0  | 165280 | 1.1503          |
| 1.1307        | 11.0  | 181808 | 1.1224          |
| 1.1689        | 12.0  | 198336 | 1.1074          |
| 1.1007        | 13.0  | 214864 | 1.0924          |
| 1.0901        | 14.0  | 231392 | 1.0659          |
| 1.0667        | 15.0  | 247920 | 1.0650          |
| 1.0434        | 16.0  | 264448 | 1.0362          |
| 1.0333        | 17.0  | 280976 | 1.0250          |
| 1.0342        | 18.0  | 297504 | 1.0198          |
| 1.0059        | 19.0  | 314032 | 0.9950          |
| 0.9719        | 20.0  | 330560 | 0.9836          |
| 0.9863        | 21.0  | 347088 | 0.9873          |
| 0.9781        | 22.0  | 363616 | 0.9724          |
| 0.9369        | 23.0  | 380144 | 0.9599          |
| 0.9578        | 24.0  | 396672 | 0.9557          |
| 0.9253        | 25.0  | 413200 | 0.9400          |
| 0.9441        | 26.0  | 429728 | 0.9222          |
| 0.9138        | 27.0  | 446256 | 0.9140          |
| 0.882         | 28.0  | 462784 | 0.9045          |
| 0.864         | 29.0  | 479312 | 0.8880          |
| 0.8632        | 30.0  | 495840 | 0.9023          |
| 0.8342        | 32.0  | 528896 | 0.8740          |
| 0.8037        | 34.0  | 561952 | 0.8647          |
| 0.8119        | 37.0  | 611536 | 0.8358          |
| 0.8011        | 38.0  | 628064 | 0.8252          |
| 0.786         | 39.0  | 644592 | 0.8228          |
| 0.7697        | 41.0  | 677648 | 0.8138          |
| 0.7485        | 42.0  | 694176 | 0.8104          |
| 0.7689        | 43.0  | 710704 | 0.8018          |
| 0.7401        | 45.0  | 743760 | 0.7957          |
| 0.7031        | 47.0  | 776816 | 0.7726          |
| 0.7578        | 48.0  | 793344 | 0.7864          |
| 0.7298        | 49.0  | 809872 | 0.7775          |
| 0.707         | 50.0  | 826400 | 0.7784          |


### Framework versions

- Transformers 4.10.3
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
