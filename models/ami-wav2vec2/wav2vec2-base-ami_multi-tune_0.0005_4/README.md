---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-tune_0.0005_4
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-tune_0.0005_4

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 3.9286
- Wer: 1.0

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer |
|:-------------:|:-----:|:-----:|:---------------:|:---:|
| 3.0115        | 0.86  | 1000  | 3.8103          | 1.0 |
| 2.9818        | 1.72  | 2000  | 3.6096          | 1.0 |
| 2.9991        | 2.59  | 3000  | 3.6555          | 1.0 |
| 2.9914        | 3.45  | 4000  | 3.6829          | 1.0 |
| 2.9958        | 4.31  | 5000  | 3.5873          | 1.0 |
| 2.9921        | 5.17  | 6000  | 3.5026          | 1.0 |
| 3.0256        | 6.03  | 7000  | 3.5531          | 1.0 |
| 2.9892        | 6.9   | 8000  | 3.6803          | 1.0 |
| 2.9994        | 7.76  | 9000  | 3.5720          | 1.0 |
| 2.9796        | 8.62  | 10000 | 3.6583          | 1.0 |
| 2.9837        | 9.48  | 11000 | 3.6397          | 1.0 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
