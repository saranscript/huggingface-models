---
license: apache-2.0
language:
- hi
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-hi
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-hi

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 2.4749
- Wer: 0.9420

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 9.8626        | 4.76  | 400  | 3.6151          | 1.0    |
| 3.5463        | 9.52  | 800  | 3.5778          | 1.0    |
| 3.4415        | 14.28 | 1200 | 3.4525          | 1.0    |
| 3.0927        | 19.05 | 1600 | 2.6220          | 0.9860 |
| 2.0573        | 23.8  | 2000 | 2.3974          | 0.9610 |
| 1.5905        | 28.57 | 2400 | 2.4427          | 0.9558 |
| 1.426         | 33.33 | 2800 | 2.4736          | 0.9475 |
| 1.3147        | 38.09 | 3200 | 2.4494          | 0.9417 |
| 1.2642        | 42.85 | 3600 | 2.4665          | 0.9450 |
| 1.2289        | 47.62 | 4000 | 2.4749          | 0.9420 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3
