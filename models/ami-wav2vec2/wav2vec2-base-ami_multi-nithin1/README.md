---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-ami_multi-nithin1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-ami_multi-nithin1

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 9.4710
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
- learning_rate: 0.0003
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer |
|:-------------:|:-----:|:-----:|:---------------:|:---:|
| 3.1594        | 1.07  | 5000  | 8.2680          | 1.0 |
| 3.1647        | 2.13  | 10000 | 7.7283          | 1.0 |
| 3.152         | 3.2   | 15000 | 8.5267          | 1.0 |
| 3.1738        | 4.27  | 20000 | 7.8057          | 1.0 |
| 3.1628        | 5.33  | 25000 | 8.4358          | 1.0 |
| 3.1314        | 6.4   | 30000 | 8.2546          | 1.0 |
| 3.1772        | 7.46  | 35000 | 8.0952          | 1.0 |
| 3.1504        | 8.53  | 40000 | 8.4454          | 1.0 |
| 3.1598        | 9.6   | 45000 | 8.0497          | 1.0 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
