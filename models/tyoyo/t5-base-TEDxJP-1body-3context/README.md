---
license: cc-by-sa-4.0
tags:
- generated_from_trainer
datasets:
- te_dx_jp
model-index:
- name: t5-base-TEDxJP-1body-3context
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base-TEDxJP-1body-3context

This model is a fine-tuned version of [sonoisa/t5-base-japanese](https://huggingface.co/sonoisa/t5-base-japanese) on the te_dx_jp dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4926
- Wer: 0.1968
- Mer: 0.1894
- Wil: 0.2793
- Wip: 0.7207
- Hits: 55899
- Substitutions: 6836
- Deletions: 3636
- Insertions: 2590
- Cer: 0.1733

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
| 0.7082        | 1.0   | 746  | 0.5637          | 0.2626 | 0.2430 | 0.3355 | 0.6645 | 54301 | 7195          | 4875      | 5358       | 0.2552 |
| 0.6213        | 2.0   | 1492 | 0.5150          | 0.2068 | 0.1994 | 0.2899 | 0.7101 | 55107 | 6861          | 4403      | 2462       | 0.1866 |
| 0.5331        | 3.0   | 2238 | 0.4945          | 0.2038 | 0.1958 | 0.2858 | 0.7142 | 55551 | 6845          | 3975      | 2705       | 0.1816 |
| 0.5185        | 4.0   | 2984 | 0.4880          | 0.2003 | 0.1929 | 0.2831 | 0.7169 | 55639 | 6860          | 3872      | 2563       | 0.1779 |
| 0.4963        | 5.0   | 3730 | 0.4858          | 0.1988 | 0.1912 | 0.2810 | 0.7190 | 55837 | 6838          | 3696      | 2662       | 0.1772 |
| 0.4625        | 6.0   | 4476 | 0.4885          | 0.1964 | 0.1894 | 0.2799 | 0.7201 | 55785 | 6875          | 3711      | 2448       | 0.1720 |
| 0.4416        | 7.0   | 5222 | 0.4898          | 0.1962 | 0.1890 | 0.2788 | 0.7212 | 55870 | 6819          | 3682      | 2522       | 0.1726 |
| 0.4287        | 8.0   | 5968 | 0.4894          | 0.1968 | 0.1894 | 0.2790 | 0.7210 | 55889 | 6804          | 3678      | 2580       | 0.1743 |
| 0.4457        | 9.0   | 6714 | 0.4909          | 0.1964 | 0.1891 | 0.2792 | 0.7208 | 55919 | 6858          | 3594      | 2586       | 0.1739 |
| 0.4068        | 10.0  | 7460 | 0.4926          | 0.1968 | 0.1894 | 0.2793 | 0.7207 | 55899 | 6836          | 3636      | 2590       | 0.1733 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
