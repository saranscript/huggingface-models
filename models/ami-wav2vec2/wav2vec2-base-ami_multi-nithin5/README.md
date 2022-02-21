---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-ami_multi-nithin5
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-ami_multi-nithin5

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5392
- Wer: 0.4481

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.8839        | 2.16  | 2500  | 1.7172          | 0.6249 |
| 1.5323        | 4.31  | 5000  | 1.4628          | 0.4930 |
| 1.4325        | 6.47  | 7500  | 1.3856          | 0.4495 |
| 1.3461        | 8.62  | 10000 | 1.3695          | 0.4350 |
| 1.3249        | 10.78 | 12500 | 1.3640          | 0.4294 |
| 1.3288        | 12.93 | 15000 | 1.3429          | 0.4220 |
| 1.2503        | 15.09 | 17500 | 1.3325          | 0.4171 |
| 1.2587        | 17.24 | 20000 | 1.3201          | 0.4108 |
| 1.2135        | 19.4  | 22500 | 1.3329          | 0.4083 |
| 1.2154        | 21.55 | 25000 | 1.3341          | 0.4057 |
| 1.2162        | 23.71 | 27500 | 1.3291          | 0.4046 |
| 1.2062        | 25.86 | 30000 | 1.3305          | 0.4031 |
| 1.1853        | 28.02 | 32500 | 1.3299          | 0.4023 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
