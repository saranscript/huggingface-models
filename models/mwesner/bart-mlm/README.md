---
tags:
- generated_from_trainer
datasets:
- null
model_index:
- name: bart-mlm
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-mlm

This model is a fine-tuned version of [mwesner/bart-mlm](https://huggingface.co/mwesner/bart-mlm) on the CNN/Dailymail dataset.
It achieves the following results on the evaluation set:
- Loss: 7.5338

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.001
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 7.5202        | 1.0   | 15237 | 7.5964          |
| 7.5151        | 2.0   | 30474 | 7.5400          |
| 7.5157        | 3.0   | 45711 | 7.5351          |
| 7.5172        | 4.0   | 60948 | 7.5317          |
| 7.5108        | 5.0   | 76185 | 7.5338          |


### Framework versions

- Transformers 4.8.1
- Pytorch 1.9.0
- Datasets 1.11.0
- Tokenizers 0.10.3
