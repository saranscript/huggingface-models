---
license: mit
tags:
- generated_from_trainer
datasets:
- pritamdeka/cord-19-abstract
metrics:
- accuracy
model-index:
- name: pubmedbert-abstract-cord19
  results:
  - task:
      name: Masked Language Modeling
      type: fill-mask
    dataset:
      name: pritamdeka/cord-19-abstract
      type: pritamdeka/cord-19-abstract
      args: fulltext
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.7246798699728464
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# PubMedBert-abstract-cord19-v2

This model is a fine-tuned version of [microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext) on the [pritamdeka/cord-19-abstract](https://huggingface.co/datasets/pritamdeka/cord-19-abstract) dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2371
- Accuracy: 0.7247

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.95) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 10000
- num_epochs: 4.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 1.27          | 0.53  | 5000  | 1.2425          | 0.7236   |
| 1.2634        | 1.06  | 10000 | 1.3123          | 0.7141   |
| 1.3041        | 1.59  | 15000 | 1.3583          | 0.7072   |
| 1.3829        | 2.12  | 20000 | 1.3590          | 0.7121   |
| 1.3069        | 2.65  | 25000 | 1.3506          | 0.7154   |
| 1.2921        | 3.18  | 30000 | 1.3448          | 0.7160   |
| 1.2731        | 3.7   | 35000 | 1.3375          | 0.7178   |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
