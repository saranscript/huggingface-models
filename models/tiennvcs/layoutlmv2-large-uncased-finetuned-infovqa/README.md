---
license: cc-by-nc-sa-4.0
tags:
- generated_from_trainer
model-index:
- name: layoutlmv2-large-uncased-finetuned-infovqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# layoutlmv2-large-uncased-finetuned-infovqa

This model is a fine-tuned version of [microsoft/layoutlmv2-large-uncased](https://huggingface.co/microsoft/layoutlmv2-large-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.2207

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 2
- eval_batch_size: 2
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 4.1829        | 0.08  | 500   | 3.6339          |
| 3.5002        | 0.16  | 1000  | 3.0721          |
| 2.9556        | 0.24  | 1500  | 2.8731          |
| 2.8939        | 0.33  | 2000  | 3.1566          |
| 2.6986        | 0.41  | 2500  | 3.1023          |
| 2.7569        | 0.49  | 3000  | 2.7743          |
| 2.6391        | 0.57  | 3500  | 2.5023          |
| 2.4277        | 0.65  | 4000  | 2.5465          |
| 2.4242        | 0.73  | 4500  | 2.4709          |
| 2.3978        | 0.82  | 5000  | 2.4019          |
| 2.2653        | 0.9   | 5500  | 2.3383          |
| 2.3916        | 0.98  | 6000  | 2.4765          |
| 1.9423        | 1.06  | 6500  | 2.3798          |
| 1.8538        | 1.14  | 7000  | 2.3628          |
| 1.8136        | 1.22  | 7500  | 2.3671          |
| 1.7808        | 1.31  | 8000  | 2.5585          |
| 1.7772        | 1.39  | 8500  | 2.5862          |
| 1.755         | 1.47  | 9000  | 2.3105          |
| 1.6529        | 1.55  | 9500  | 2.2417          |
| 1.6956        | 1.63  | 10000 | 2.1755          |
| 1.5713        | 1.71  | 10500 | 2.2917          |
| 1.565         | 1.79  | 11000 | 2.0838          |
| 1.615         | 1.88  | 11500 | 2.2111          |
| 1.5249        | 1.96  | 12000 | 2.2207          |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.8.0+cu101
- Datasets 1.15.1
- Tokenizers 0.10.3
