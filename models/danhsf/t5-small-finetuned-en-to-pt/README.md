---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: t5-small-finetuned-en-to-pt
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-en-to-pt

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3295
- Bleu: 5.6807
- Gen Len: 18.6772

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu   | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:-------:|
| 0.5787        | 1.0   | 6250  | 0.4928          | 4.1007 | 18.638  |
| 0.5089        | 2.0   | 12500 | 0.4463          | 4.3492 | 18.663  |
| 0.4652        | 3.0   | 18750 | 0.4215          | 4.68   | 18.6652 |
| 0.4353        | 4.0   | 25000 | 0.3980          | 4.8172 | 18.6708 |
| 0.4042        | 5.0   | 31250 | 0.3799          | 4.9719 | 18.6514 |
| 0.3734        | 6.0   | 37500 | 0.3676          | 5.2226 | 18.6572 |
| 0.3396        | 7.0   | 43750 | 0.3513          | 5.2693 | 18.6596 |
| 0.308         | 8.0   | 50000 | 0.3400          | 5.4546 | 18.676  |
| 0.2767        | 9.0   | 56250 | 0.3331          | 5.5649 | 18.6708 |
| 0.2424        | 10.0  | 62500 | 0.3295          | 5.6807 | 18.6772 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
