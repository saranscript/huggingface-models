---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: custom_german
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# custom_german

This model is a fine-tuned version of [flozi00/wav2vec-xlsr-german](https://huggingface.co/flozi00/wav2vec-xlsr-german) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 4.6832
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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 5
- num_epochs: 30

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer |
|:-------------:|:-----:|:----:|:---------------:|:---:|
| 8.7718        | 5.0   | 5    | 8.5148          | 1.0 |
| 3.7125        | 10.0  | 10   | 5.4304          | 1.0 |
| 2.7679        | 15.0  | 15   | 5.0388          | 1.0 |
| 2.0516        | 20.0  | 20   | 4.4628          | 1.0 |
| 1.6702        | 25.0  | 25   | 4.5341          | 1.0 |
| 1.515         | 30.0  | 30   | 4.6832          | 1.0 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu102
- Datasets 1.13.3
- Tokenizers 0.10.3
