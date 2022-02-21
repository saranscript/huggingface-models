---
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: unispeech-sat-base-plus-timit-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# unispeech-sat-base-plus-timit-ft

This model is a fine-tuned version of [microsoft/unispeech-sat-base-plus](https://huggingface.co/microsoft/unispeech-sat-base-plus) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6549
- Wer: 0.4051

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
- train_batch_size: 32
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 20.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.3838        | 0.69  | 100  | 3.2528          | 1.0    |
| 2.9608        | 1.38  | 200  | 2.9682          | 1.0    |
| 2.9574        | 2.07  | 300  | 2.9346          | 1.0    |
| 2.8555        | 2.76  | 400  | 2.7612          | 1.0    |
| 1.7418        | 3.45  | 500  | 1.5732          | 0.9857 |
| 0.9606        | 4.14  | 600  | 1.0014          | 0.7052 |
| 0.8334        | 4.83  | 700  | 0.7691          | 0.6161 |
| 0.852         | 5.52  | 800  | 0.7169          | 0.5997 |
| 0.5707        | 6.21  | 900  | 0.6821          | 0.5527 |
| 0.4235        | 6.9   | 1000 | 0.6078          | 0.5140 |
| 0.4357        | 7.59  | 1100 | 0.5927          | 0.4982 |
| 0.5004        | 8.28  | 1200 | 0.5814          | 0.4826 |
| 0.3757        | 8.97  | 1300 | 0.5951          | 0.4643 |
| 0.2579        | 9.66  | 1400 | 0.5990          | 0.4581 |
| 0.2087        | 10.34 | 1500 | 0.5864          | 0.4488 |
| 0.3155        | 11.03 | 1600 | 0.5836          | 0.4464 |
| 0.2701        | 11.72 | 1700 | 0.6045          | 0.4348 |
| 0.172         | 12.41 | 1800 | 0.6494          | 0.4344 |
| 0.1529        | 13.1  | 1900 | 0.5915          | 0.4241 |
| 0.2411        | 13.79 | 2000 | 0.6156          | 0.4246 |
| 0.2348        | 14.48 | 2100 | 0.6363          | 0.4206 |
| 0.1429        | 15.17 | 2200 | 0.6394          | 0.4161 |
| 0.1151        | 15.86 | 2300 | 0.6186          | 0.4167 |
| 0.1723        | 16.55 | 2400 | 0.6498          | 0.4124 |
| 0.1997        | 17.24 | 2500 | 0.6541          | 0.4076 |
| 0.1297        | 17.93 | 2600 | 0.6546          | 0.4117 |
| 0.101         | 18.62 | 2700 | 0.6471          | 0.4075 |
| 0.1272        | 19.31 | 2800 | 0.6586          | 0.4065 |
| 0.1901        | 20.0  | 2900 | 0.6549          | 0.4051 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
