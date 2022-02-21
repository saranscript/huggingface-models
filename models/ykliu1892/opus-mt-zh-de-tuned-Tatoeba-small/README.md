---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-zh-de-tuned-Tatoeba-small
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-zh-de-tuned-Tatoeba-small

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-zh-de](https://huggingface.co/Helsinki-NLP/opus-mt-zh-de) on a refined dataset of Tatoeba German - Chinese corpus https://github.com/Helsinki-NLP/Tatoeba-Challenge/blob/master/data/README.md.
It achieves the following results on the evaluation set:
- Loss: 2.2703
- Bleu: 16.504
- Gen Len: 16.6531

## Model description

More information needed

## Intended uses & limitations

Prefix used during fine-tuning: "将中文翻译成德语". This prefix is also recommended in prediction.

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:-------:|:-------:|
| 2.7229        | 0.24  | 16000  | 2.5605          | 14.1956 | 16.2206 |
| 2.5988        | 0.49  | 32000  | 2.4447          | 14.8619 | 16.2726 |
| 2.515         | 0.73  | 48000  | 2.3817          | 15.3212 | 16.2823 |
| 2.4683        | 0.97  | 64000  | 2.3367          | 15.9043 | 16.7138 |
| 2.3873        | 1.22  | 80000  | 2.3115          | 16.1037 | 16.6369 |
| 2.3792        | 1.46  | 96000  | 2.2919          | 16.2957 | 16.6304 |
| 2.3626        | 1.7   | 112000 | 2.2790          | 16.2995 | 16.6235 |
| 2.3353        | 1.95  | 128000 | 2.2703          | 16.504  | 16.6531 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
