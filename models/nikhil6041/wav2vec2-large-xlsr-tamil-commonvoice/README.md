---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xlsr-tamil-commonvoice
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-tamil-commonvoice

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6145
- Wer: 0.8512

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
- lr_scheduler_warmup_steps: 200
- num_epochs: 20
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 12.0478       | 1.05  | 100  | 3.3867          | 1.0    |
| 3.2522        | 2.11  | 200  | 3.2770          | 1.0    |
| 3.1689        | 3.16  | 300  | 3.1135          | 1.0039 |
| 2.9278        | 4.21  | 400  | 2.0485          | 1.3109 |
| 1.3592        | 5.26  | 500  | 0.8044          | 1.0988 |
| 0.7472        | 6.32  | 600  | 0.6571          | 0.9474 |
| 0.5842        | 7.37  | 700  | 0.6079          | 0.9477 |
| 0.4831        | 8.42  | 800  | 0.6083          | 0.9491 |
| 0.4259        | 9.47  | 900  | 0.5916          | 0.8973 |
| 0.3817        | 10.53 | 1000 | 0.6070          | 0.9147 |
| 0.338         | 11.58 | 1100 | 0.5873          | 0.8617 |
| 0.3123        | 12.63 | 1200 | 0.5983          | 0.8844 |
| 0.287         | 13.68 | 1300 | 0.6146          | 0.8988 |
| 0.2706        | 14.74 | 1400 | 0.6068          | 0.8754 |
| 0.2505        | 15.79 | 1500 | 0.5996          | 0.8638 |
| 0.2412        | 16.84 | 1600 | 0.6106          | 0.8481 |
| 0.2176        | 17.89 | 1700 | 0.6152          | 0.8520 |
| 0.2255        | 18.95 | 1800 | 0.6150          | 0.8540 |
| 0.216         | 20.0  | 1900 | 0.6145          | 0.8512 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu102
- Datasets 1.13.3
- Tokenizers 0.10.3
