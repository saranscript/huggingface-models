---
license: mit
tags:
- generated_from_trainer
datasets:
- pritamdeka/cord-19-abstract
model-index:
- name: PubMedBert-abstract-cord19
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pubmedbert-abstract-cord19

This model is a fine-tuned version of [microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext) on the [pritamdeka/cord-19-abstract](https://huggingface.co/datasets/pritamdeka/cord-19-abstract) dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3005

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
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 10000
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss |
|:-------------:|:-----:|:------:|:---------------:|
| 1.3774        | 0.15  | 5000   | 1.3212          |
| 1.3937        | 0.29  | 10000  | 1.4059          |
| 1.6812        | 0.44  | 15000  | 1.6174          |
| 1.4712        | 0.59  | 20000  | 1.4383          |
| 1.4293        | 0.73  | 25000  | 1.4356          |
| 1.4155        | 0.88  | 30000  | 1.4283          |
| 1.3963        | 1.03  | 35000  | 1.4135          |
| 1.3718        | 1.18  | 40000  | 1.3948          |
| 1.369         | 1.32  | 45000  | 1.3961          |
| 1.354         | 1.47  | 50000  | 1.3788          |
| 1.3399        | 1.62  | 55000  | 1.3866          |
| 1.3289        | 1.76  | 60000  | 1.3630          |
| 1.3155        | 1.91  | 65000  | 1.3609          |
| 1.2976        | 2.06  | 70000  | 1.3489          |
| 1.2783        | 2.2   | 75000  | 1.3333          |
| 1.2696        | 2.35  | 80000  | 1.3260          |
| 1.2607        | 2.5   | 85000  | 1.3232          |
| 1.2547        | 2.64  | 90000  | 1.3034          |
| 1.2495        | 2.79  | 95000  | 1.3035          |
| 1.2404        | 2.94  | 100000 | 1.3029          |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
