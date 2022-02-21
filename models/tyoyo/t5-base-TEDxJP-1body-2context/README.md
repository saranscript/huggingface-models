---
license: cc-by-sa-4.0
tags:
- generated_from_trainer
datasets:
- te_dx_jp
model-index:
- name: t5-base-TEDxJP-1body-2context
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base-TEDxJP-1body-2context

This model is a fine-tuned version of [sonoisa/t5-base-japanese](https://huggingface.co/sonoisa/t5-base-japanese) on the te_dx_jp dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4968
- Wer: 0.1969
- Mer: 0.1895
- Wil: 0.2801
- Wip: 0.7199
- Hits: 55902
- Substitutions: 6899
- Deletions: 3570
- Insertions: 2599
- Cer: 0.1727

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
| 0.7136        | 1.0   | 746  | 0.5716          | 0.2512 | 0.2345 | 0.3279 | 0.6721 | 54430 | 7249          | 4692      | 4731       | 0.2344 |
| 0.6267        | 2.0   | 1492 | 0.5152          | 0.2088 | 0.2005 | 0.2917 | 0.7083 | 55245 | 6949          | 4177      | 2732       | 0.2009 |
| 0.5416        | 3.0   | 2238 | 0.4969          | 0.2025 | 0.1948 | 0.2851 | 0.7149 | 55575 | 6871          | 3925      | 2646       | 0.1802 |
| 0.5223        | 4.0   | 2984 | 0.4915          | 0.1989 | 0.1917 | 0.2816 | 0.7184 | 55652 | 6826          | 3893      | 2481       | 0.1754 |
| 0.4985        | 5.0   | 3730 | 0.4929          | 0.1991 | 0.1916 | 0.2814 | 0.7186 | 55759 | 6828          | 3784      | 2603       | 0.1753 |
| 0.4675        | 6.0   | 4476 | 0.4910          | 0.1969 | 0.1897 | 0.2799 | 0.7201 | 55834 | 6859          | 3678      | 2534       | 0.1756 |
| 0.445         | 7.0   | 5222 | 0.4940          | 0.1955 | 0.1884 | 0.2782 | 0.7218 | 55881 | 6821          | 3669      | 2485       | 0.1712 |
| 0.4404        | 8.0   | 5968 | 0.4932          | 0.1979 | 0.1903 | 0.2801 | 0.7199 | 55881 | 6828          | 3662      | 2643       | 0.1742 |
| 0.4525        | 9.0   | 6714 | 0.4951          | 0.1968 | 0.1893 | 0.2799 | 0.7201 | 55939 | 6897          | 3535      | 2632       | 0.1740 |
| 0.4077        | 10.0  | 7460 | 0.4968          | 0.1969 | 0.1895 | 0.2801 | 0.7199 | 55902 | 6899          | 3570      | 2599       | 0.1727 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
