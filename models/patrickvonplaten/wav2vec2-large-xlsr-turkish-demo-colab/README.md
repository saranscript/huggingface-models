---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xlsr-turkish-demo-colab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-turkish-demo-colab

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4055
- Wer: 0.4800

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
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.0179        | 4.21  | 400  | 1.4935          | 1.0249 |
| 0.7075        | 8.42  | 800  | 0.4546          | 0.6071 |
| 0.3072        | 12.63 | 1200 | 0.3947          | 0.5401 |
| 0.2145        | 16.84 | 1600 | 0.4049          | 0.5194 |
| 0.1647        | 21.05 | 2000 | 0.4199          | 0.5003 |
| 0.1338        | 25.26 | 2400 | 0.4144          | 0.4859 |
| 0.116         | 29.47 | 2800 | 0.4055          | 0.4800 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1+cu102
- Datasets 1.13.3
- Tokenizers 0.10.3
