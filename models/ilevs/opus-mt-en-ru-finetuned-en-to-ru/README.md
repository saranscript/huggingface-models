---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-en-ru-finetuned-en-to-ru
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-en-ru-finetuned-en-to-ru

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-ru](https://huggingface.co/Helsinki-NLP/opus-mt-en-ru) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.7682
- Bleu: 14.6112
- Gen Len: 7.202

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
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|
| 2.3198        | 1.0   | 4956  | 2.1261          | 9.5339  | 6.7709  |
| 1.9732        | 2.0   | 9912  | 1.9639          | 10.4715 | 7.1254  |
| 1.7127        | 3.0   | 14868 | 1.8780          | 11.6128 | 7.1106  |
| 1.5614        | 4.0   | 19824 | 1.8367          | 12.8389 | 7.0468  |
| 1.4276        | 5.0   | 24780 | 1.8040          | 13.7423 | 7.0403  |
| 1.3096        | 6.0   | 29736 | 1.7820          | 14.1469 | 7.0555  |
| 1.2381        | 7.0   | 34692 | 1.7761          | 13.9987 | 7.2225  |
| 1.1784        | 8.0   | 39648 | 1.7725          | 14.4675 | 7.1799  |
| 1.1376        | 9.0   | 44604 | 1.7692          | 14.4937 | 7.1957  |
| 1.0862        | 10.0  | 49560 | 1.7682          | 14.6112 | 7.202   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
