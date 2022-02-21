---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-base-960h-dementiabank
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-960h-dementiabank

This model is a fine-tuned version of [facebook/wav2vec2-base-960h](https://huggingface.co/facebook/wav2vec2-base-960h) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2133.3391
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
- learning_rate: 0.005
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer |
|:-------------:|:-----:|:----:|:---------------:|:---:|
| 677.9684      | 6.25  | 200  | 2157.9404       | 1.0 |
| 543.9684      | 12.5  | 400  | 2145.2729       | 1.0 |
| 920.0218      | 18.75 | 600  | 2156.7012       | 1.0 |
| 699.6337      | 25.0  | 800  | 2381.3455       | 1.0 |
| 571.8986      | 31.25 | 1000 | 2173.7847       | 1.0 |
| 577.2243      | 37.5  | 1200 | 2149.5928       | 1.0 |
| 525.5096      | 43.75 | 1400 | 2152.0005       | 1.0 |
| 510.4062      | 50.0  | 1600 | 2133.3391       | 1.0 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
