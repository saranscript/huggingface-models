---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- new_dataset
metrics:
- sacrebleu
model-index:
- name: ted_mt-Spanish-to-Italian
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: new_dataset
      type: new_dataset
      args: ted_mt
    metrics:
    - name: Sacrebleu
      type: sacrebleu
      value: 33.6712
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# ted_mt-Spanish-to-Italian

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-es-it](https://huggingface.co/Helsinki-NLP/opus-mt-es-it) on the on the [mtdata neulabTedTalks](https://aclanthology.org/2021.acl-demo.37/) dataset.

It achieves the following results on the evaluation set:
- Loss: 1.3533
- Sacrebleu: 33.6712
- Gen Len: 28.004

## Model description

model name: opus-mt-es-it-finetuned-Spanish-to-Italian

Trained on: [Ted Talks](https://huggingface.co/datasets/frtna/ted_mt) 
<br>
train dataset length = **2891** 


Evaluated on: [OPUS Tatoeba](https://github.com/Helsinki-NLP/Tatoeba-Challenge/blob/master/README-v2020-07-28.md)

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
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Sacrebleu | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:-------:|
| No log        | 1.0   | 181  | 1.3779          | 32.4532   | 28.1355 |
| No log        | 2.0   | 362  | 1.3551          | 33.167    | 27.9935 |
| 1.3581        | 3.0   | 543  | 1.3533          | 33.438    | 28.2444 |
| 1.3581        | 4.0   | 724  | 1.3537          | 33.5186   | 28.0331 |
| 1.3581        | 5.0   | 905  | 1.3533          | 33.6712   | 28.004  |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
