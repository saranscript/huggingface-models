---
license: cc-by-sa-4.0
tags:
- generated_from_trainer
datasets:
- te_dx_jp
model-index:
- name: t5-base-TEDxJP-11body-0context
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base-TEDxJP-11body-0context

This model is a fine-tuned version of [sonoisa/t5-base-japanese](https://huggingface.co/sonoisa/t5-base-japanese) on the te_dx_jp dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8068
- Wer: 0.1976
- Mer: 0.1904
- Wil: 0.2816
- Wip: 0.7184
- Hits: 602335
- Substitutions: 75050
- Deletions: 39435
- Insertions: 27185
- Cer: 0.1625

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 64
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Mer    | Wil    | Wip    | Hits   | Substitutions | Deletions | Insertions | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|:------:|:------:|:------:|:-------------:|:---------:|:----------:|:------:|
| 0.8909        | 1.0   | 746  | 0.7722          | 0.3120 | 0.2861 | 0.3989 | 0.6011 | 558138 | 99887         | 58795     | 64983      | 0.2652 |
| 0.6786        | 2.0   | 1492 | 0.7021          | 0.2226 | 0.2122 | 0.3069 | 0.6931 | 592242 | 78773         | 45805     | 34978      | 0.1862 |
| 0.5627        | 3.0   | 2238 | 0.6996          | 0.2104 | 0.2016 | 0.2942 | 0.7058 | 597381 | 76593         | 42846     | 31392      | 0.1752 |
| 0.489         | 4.0   | 2984 | 0.7161          | 0.2030 | 0.1952 | 0.2865 | 0.7135 | 599808 | 75155         | 41857     | 28506      | 0.1684 |
| 0.4355        | 5.0   | 3730 | 0.7389          | 0.2000 | 0.1924 | 0.2837 | 0.7163 | 601815 | 75247         | 39758     | 28335      | 0.1651 |
| 0.3836        | 6.0   | 4476 | 0.7537          | 0.1992 | 0.1918 | 0.2829 | 0.7171 | 601846 | 75046         | 39928     | 27815      | 0.1640 |
| 0.3617        | 7.0   | 5222 | 0.7743          | 0.1995 | 0.1918 | 0.2832 | 0.7168 | 602287 | 75268         | 39265     | 28445      | 0.1642 |
| 0.3258        | 8.0   | 5968 | 0.7907          | 0.1971 | 0.1899 | 0.2809 | 0.7191 | 602800 | 74887         | 39133     | 27258      | 0.1620 |
| 0.3225        | 9.0   | 6714 | 0.8035          | 0.1981 | 0.1908 | 0.2823 | 0.7177 | 602418 | 75372         | 39030     | 27625      | 0.1630 |
| 0.3162        | 10.0  | 7460 | 0.8068          | 0.1976 | 0.1904 | 0.2816 | 0.7184 | 602335 | 75050         | 39435     | 27185      | 0.1625 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
