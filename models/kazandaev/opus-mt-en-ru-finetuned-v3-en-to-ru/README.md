---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: opus-mt-en-ru-finetuned-v3-en-to-ru
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# opus-mt-en-ru-finetuned-v3-en-to-ru

This model is a fine-tuned version of [kazandaev/opus-mt-en-ru-finetuned-v3-en-to-ru](https://huggingface.co/kazandaev/opus-mt-en-ru-finetuned-v3-en-to-ru) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7428
- Bleu: 40.8902
- Gen Len: 29.2072

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 6e-06
- train_batch_size: 50
- eval_batch_size: 50
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:-------:|:-------:|
| 0.8389        | 1.0   | 42137  | 0.7550          | 40.6244 | 29.1945 |
| 0.8416        | 2.0   | 84274  | 0.7529          | 40.1075 | 29.3087 |
| 0.8395        | 3.0   | 126411 | 0.7499          | 40.6498 | 29.2431 |
| 0.8525        | 4.0   | 168548 | 0.7453          | 41.019  | 29.1881 |
| 0.8544        | 5.0   | 210685 | 0.7434          | 40.8079 | 29.214  |
| 0.8469        | 6.0   | 252822 | 0.7428          | 40.8902 | 29.2072 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
