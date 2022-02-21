---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-base-cynthia-tedlium-2500-v2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-cynthia-tedlium-2500-v2

This model is a fine-tuned version of [facebook/wav2vec2-base-960h](https://huggingface.co/facebook/wav2vec2-base-960h) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6425
- Wer: 0.2033

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.1196        | 6.58  | 500  | 0.6498          | 0.2103 |
| 0.1176        | 13.16 | 1000 | 0.6490          | 0.2169 |
| 0.1227        | 19.73 | 1500 | 0.6241          | 0.2127 |
| 0.1078        | 26.31 | 2000 | 0.6359          | 0.2118 |
| 0.0956        | 32.89 | 2500 | 0.6330          | 0.2073 |
| 0.1008        | 39.47 | 3000 | 0.6816          | 0.2036 |
| 0.09          | 46.05 | 3500 | 0.6425          | 0.2033 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu113
- Datasets 1.13.3
- Tokenizers 0.10.3
