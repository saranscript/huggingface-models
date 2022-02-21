---
tags:
- generated_from_trainer
model-index:
- name: model_pretrained
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# model_pretrained

This model is a fine-tuned version of [Jean-Baptiste/camembert-ner](https://huggingface.co/Jean-Baptiste/camembert-ner) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5619

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
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step   | Validation Loss |
|:-------------:|:-----:|:------:|:---------------:|
| 1.9603        | 1.0   | 100346 | 1.8005          |
| 1.7032        | 2.0   | 200692 | 1.6460          |
| 1.5879        | 3.0   | 301038 | 1.5570          |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.0
- Tokenizers 0.10.3
