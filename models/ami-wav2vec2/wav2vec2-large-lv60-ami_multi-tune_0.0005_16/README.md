---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-large-lv60-ami_multi-tune_0.0005_16
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-lv60-ami_multi-tune_0.0005_16

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4670
- Wer: 0.4379

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
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 16
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.2775        | 1.72  | 1000 | 1.2890          | 0.4219 |
| 1.0728        | 3.45  | 2000 | 1.2016          | 0.4005 |
| 0.9245        | 5.17  | 3000 | 1.1885          | 0.3961 |
| 0.8506        | 6.9   | 4000 | 1.2045          | 0.3909 |
| 0.7202        | 8.62  | 5000 | 1.2507          | 0.3944 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
