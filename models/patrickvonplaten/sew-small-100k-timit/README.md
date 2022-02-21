---
license: apache-2.0
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: sew-small-100k-timit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-small-100k-timit

This model is a fine-tuned version of [asapp/sew-small-100k](https://huggingface.co/asapp/sew-small-100k) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4926
- Wer: 0.2988

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
| 3.071         | 0.69  | 100  | 3.0262          | 1.0    |
| 2.9304        | 1.38  | 200  | 2.9297          | 1.0    |
| 2.8823        | 2.07  | 300  | 2.8367          | 1.0    |
| 1.5668        | 2.76  | 400  | 1.2310          | 0.8807 |
| 0.7422        | 3.45  | 500  | 0.7080          | 0.5957 |
| 0.4121        | 4.14  | 600  | 0.5829          | 0.5073 |
| 0.3981        | 4.83  | 700  | 0.5153          | 0.4461 |
| 0.5038        | 5.52  | 800  | 0.4908          | 0.4151 |
| 0.2899        | 6.21  | 900  | 0.5122          | 0.4111 |
| 0.2198        | 6.9   | 1000 | 0.4908          | 0.3803 |
| 0.2129        | 7.59  | 1100 | 0.4668          | 0.3789 |
| 0.3007        | 8.28  | 1200 | 0.4788          | 0.3562 |
| 0.2264        | 8.97  | 1300 | 0.5113          | 0.3635 |
| 0.1536        | 9.66  | 1400 | 0.4950          | 0.3441 |
| 0.1206        | 10.34 | 1500 | 0.5062          | 0.3421 |
| 0.2021        | 11.03 | 1600 | 0.4900          | 0.3283 |
| 0.1458        | 11.72 | 1700 | 0.5019          | 0.3307 |
| 0.1151        | 12.41 | 1800 | 0.4989          | 0.3270 |
| 0.0985        | 13.1  | 1900 | 0.4925          | 0.3173 |
| 0.1412        | 13.79 | 2000 | 0.4868          | 0.3125 |
| 0.1579        | 14.48 | 2100 | 0.4983          | 0.3147 |
| 0.1043        | 15.17 | 2200 | 0.4914          | 0.3091 |
| 0.0773        | 15.86 | 2300 | 0.4858          | 0.3102 |
| 0.1327        | 16.55 | 2400 | 0.5084          | 0.3064 |
| 0.1281        | 17.24 | 2500 | 0.5017          | 0.3025 |
| 0.0845        | 17.93 | 2600 | 0.5001          | 0.3012 |
| 0.0717        | 18.62 | 2700 | 0.4894          | 0.3004 |
| 0.0835        | 19.31 | 2800 | 0.4963          | 0.2998 |
| 0.1181        | 20.0  | 2900 | 0.4926          | 0.2988 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
