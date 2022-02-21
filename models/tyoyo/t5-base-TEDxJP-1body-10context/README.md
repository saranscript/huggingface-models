---
license: cc-by-sa-4.0
tags:
- generated_from_trainer
datasets:
- te_dx_jp
model-index:
- name: t5-base-TEDxJP-1body-10context
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base-TEDxJP-1body-10context

This model is a fine-tuned version of [sonoisa/t5-base-japanese](https://huggingface.co/sonoisa/t5-base-japanese) on the te_dx_jp dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3833
- Wer: 0.1983
- Mer: 0.1900
- Wil: 0.2778
- Wip: 0.7222
- Hits: 56229
- Substitutions: 6686
- Deletions: 3593
- Insertions: 2909
- Cer: 0.1823

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

| Training Loss | Epoch | Step | Validation Loss | Wer    | Mer    | Wil    | Wip    | Hits  | Substitutions | Deletions | Insertions | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|:------:|:------:|:-----:|:-------------:|:---------:|:----------:|:------:|
| 0.5641        | 1.0   | 746  | 0.4426          | 0.2336 | 0.2212 | 0.3143 | 0.6857 | 54711 | 7183          | 4614      | 3742       | 0.2238 |
| 0.4867        | 2.0   | 1492 | 0.4017          | 0.2045 | 0.1972 | 0.2863 | 0.7137 | 55378 | 6764          | 4366      | 2470       | 0.1853 |
| 0.4257        | 3.0   | 2238 | 0.3831          | 0.2008 | 0.1933 | 0.2826 | 0.7174 | 55715 | 6788          | 4005      | 2560       | 0.1784 |
| 0.4038        | 4.0   | 2984 | 0.3797          | 0.1963 | 0.1890 | 0.2776 | 0.7224 | 56028 | 6731          | 3749      | 2578       | 0.1748 |
| 0.3817        | 5.0   | 3730 | 0.3769          | 0.1944 | 0.1877 | 0.2758 | 0.7242 | 55926 | 6663          | 3919      | 2345       | 0.1730 |
| 0.3467        | 6.0   | 4476 | 0.3806          | 0.2111 | 0.2002 | 0.2876 | 0.7124 | 56082 | 6688          | 3738      | 3616       | 0.1916 |
| 0.3361        | 7.0   | 5222 | 0.3797          | 0.1977 | 0.1897 | 0.2780 | 0.7220 | 56173 | 6721          | 3614      | 2816       | 0.1785 |
| 0.3107        | 8.0   | 5968 | 0.3814          | 0.1993 | 0.1910 | 0.2792 | 0.7208 | 56167 | 6720          | 3621      | 2916       | 0.1839 |
| 0.3141        | 9.0   | 6714 | 0.3820          | 0.1991 | 0.1907 | 0.2787 | 0.7213 | 56201 | 6709          | 3598      | 2933       | 0.1859 |
| 0.3122        | 10.0  | 7460 | 0.3833          | 0.1983 | 0.1900 | 0.2778 | 0.7222 | 56229 | 6686          | 3593      | 2909       | 0.1823 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
