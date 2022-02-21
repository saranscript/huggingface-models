---
license: gpl-3.0
tags:
- generated_from_trainer
metrics:
- matthews_correlation
model-index:
- name: IceBERT-finetuned-iec-sentence-bs16
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# IceBERT-finetuned-iec-sentence-bs16

This model is a fine-tuned version of [vesteinn/IceBERT](https://huggingface.co/vesteinn/IceBERT) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2508
- Matthews Correlation: 0.8169

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Matthews Correlation |
|:-------------:|:-----:|:-----:|:---------------:|:--------------------:|
| 0.5278        | 1.0   | 3640  | 0.4777          | 0.5396               |
| 0.4648        | 2.0   | 7280  | 0.3886          | 0.6437               |
| 0.3807        | 3.0   | 10920 | 0.3478          | 0.7060               |
| 0.3061        | 4.0   | 14560 | 0.2523          | 0.8083               |
| 0.2477        | 5.0   | 18200 | 0.2508          | 0.8169               |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.8.0
- Datasets 1.15.1
- Tokenizers 0.10.3
