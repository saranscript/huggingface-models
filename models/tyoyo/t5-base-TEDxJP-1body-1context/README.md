---
license: cc-by-sa-4.0
tags:
- generated_from_trainer
datasets:
- te_dx_jp
model-index:
- name: t5-base-TEDxJP-1body-1context
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base-TEDxJP-1body-1context

This model is a fine-tuned version of [sonoisa/t5-base-japanese](https://huggingface.co/sonoisa/t5-base-japanese) on the te_dx_jp dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5061
- Wer: 0.1990
- Mer: 0.1913
- Wil: 0.2823
- Wip: 0.7177
- Hits: 55830
- Substitutions: 6943
- Deletions: 3598
- Insertions: 2664
- Cer: 0.1763

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
| 0.7277        | 1.0   | 746  | 0.5799          | 0.2384 | 0.2256 | 0.3188 | 0.6812 | 54323 | 7170          | 4878      | 3777       | 0.2371 |
| 0.6278        | 2.0   | 1492 | 0.5254          | 0.2070 | 0.1997 | 0.2905 | 0.7095 | 55045 | 6885          | 4441      | 2412       | 0.1962 |
| 0.5411        | 3.0   | 2238 | 0.5076          | 0.2022 | 0.1950 | 0.2858 | 0.7142 | 55413 | 6902          | 4056      | 2463       | 0.1805 |
| 0.53          | 4.0   | 2984 | 0.5020          | 0.1979 | 0.1911 | 0.2814 | 0.7186 | 55599 | 6849          | 3923      | 2362       | 0.1761 |
| 0.5094        | 5.0   | 3730 | 0.4999          | 0.1987 | 0.1915 | 0.2828 | 0.7172 | 55651 | 6944          | 3776      | 2465       | 0.1742 |
| 0.4783        | 6.0   | 4476 | 0.5016          | 0.1985 | 0.1914 | 0.2826 | 0.7174 | 55684 | 6947          | 3740      | 2490       | 0.1753 |
| 0.4479        | 7.0   | 5222 | 0.5035          | 0.1976 | 0.1905 | 0.2819 | 0.7181 | 55726 | 6961          | 3684      | 2468       | 0.1733 |
| 0.4539        | 8.0   | 5968 | 0.5022          | 0.1967 | 0.1896 | 0.2807 | 0.7193 | 55795 | 6938          | 3638      | 2477       | 0.1729 |
| 0.4632        | 9.0   | 6714 | 0.5034          | 0.1991 | 0.1913 | 0.2824 | 0.7176 | 55844 | 6942          | 3585      | 2687       | 0.1758 |
| 0.4201        | 10.0  | 7460 | 0.5061          | 0.1990 | 0.1913 | 0.2823 | 0.7177 | 55830 | 6943          | 3598      | 2664       | 0.1763 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
