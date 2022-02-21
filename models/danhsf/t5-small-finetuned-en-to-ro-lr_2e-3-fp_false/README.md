---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wmt16
metrics:
- bleu
model-index:
- name: t5-small-finetuned-en-to-ro-lr_2e-3-fp_false
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: wmt16
      type: wmt16
      args: ro-en
    metrics:
    - name: Bleu
      type: bleu
      value: 7.1921
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-en-to-ro-lr_2e-3-fp_false

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wmt16 dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4239
- Bleu: 7.1921
- Gen Len: 18.2611

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.002
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:-------:|
| 0.8922        | 0.05  | 2000  | 1.7000          | 6.5274 | 18.2656 |
| 0.8621        | 0.1   | 4000  | 1.6409          | 6.6411 | 18.2311 |
| 0.8433        | 0.16  | 6000  | 1.6396          | 6.6601 | 18.2596 |
| 0.8297        | 0.21  | 8000  | 1.6304          | 6.7129 | 18.2581 |
| 0.8006        | 0.26  | 10000 | 1.6022          | 6.6067 | 18.2816 |
| 0.793         | 0.31  | 12000 | 1.5999          | 6.551  | 18.2631 |
| 0.774         | 0.37  | 14000 | 1.5586          | 6.7105 | 18.2661 |
| 0.7618        | 0.42  | 16000 | 1.5769          | 6.7278 | 18.2526 |
| 0.7463        | 0.47  | 18000 | 1.5625          | 6.6972 | 18.2201 |
| 0.7394        | 0.52  | 20000 | 1.5377          | 6.936  | 18.2491 |
| 0.7203        | 0.58  | 22000 | 1.5191          | 7.0205 | 18.2731 |
| 0.7158        | 0.63  | 24000 | 1.5055          | 6.835  | 18.2506 |
| 0.688         | 0.68  | 26000 | 1.4779          | 7.0534 | 18.2716 |
| 0.678         | 0.73  | 28000 | 1.4691          | 6.9735 | 18.2616 |
| 0.6677        | 0.79  | 30000 | 1.4702          | 7.0359 | 18.2496 |
| 0.6568        | 0.84  | 32000 | 1.4534          | 6.9982 | 18.2556 |
| 0.6475        | 0.89  | 34000 | 1.4427          | 7.0443 | 18.2466 |
| 0.6395        | 0.94  | 36000 | 1.4265          | 7.1205 | 18.2721 |
| 0.6319        | 1.0   | 38000 | 1.4239          | 7.1921 | 18.2611 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
