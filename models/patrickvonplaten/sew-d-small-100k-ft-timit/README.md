---
license: apache-2.0
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: sew-d-small-100k-ft-timit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-d-small-100k-ft-timit

This model is a fine-tuned version of [asapp/sew-d-small-100k](https://huggingface.co/asapp/sew-d-small-100k) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 1.7482
- Wer: 0.7987

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
| 4.2068        | 0.69  | 100  | 4.0802          | 1.0    |
| 2.9805        | 1.38  | 200  | 2.9792          | 1.0    |
| 2.9781        | 2.07  | 300  | 2.9408          | 1.0    |
| 2.9655        | 2.76  | 400  | 2.9143          | 1.0    |
| 2.8953        | 3.45  | 500  | 2.8775          | 1.0    |
| 2.7719        | 4.14  | 600  | 2.7815          | 0.9999 |
| 2.6531        | 4.83  | 700  | 2.6375          | 1.0065 |
| 2.6425        | 5.52  | 800  | 2.5602          | 1.0210 |
| 2.3963        | 6.21  | 900  | 2.4665          | 1.0591 |
| 2.1447        | 6.9   | 1000 | 2.2792          | 0.9848 |
| 2.2719        | 7.59  | 1100 | 2.2237          | 0.9465 |
| 2.3629        | 8.28  | 1200 | 2.1058          | 0.8907 |
| 2.0913        | 8.97  | 1300 | 2.0113          | 0.9070 |
| 1.8334        | 9.66  | 1400 | 1.9466          | 0.8177 |
| 1.6608        | 10.34 | 1500 | 1.9217          | 0.8698 |
| 2.2194        | 11.03 | 1600 | 1.9091          | 0.8727 |
| 1.9002        | 11.72 | 1700 | 1.8746          | 0.8332 |
| 1.6268        | 12.41 | 1800 | 1.8782          | 0.7951 |
| 1.6455        | 13.1  | 1900 | 1.8230          | 0.8225 |
| 2.0308        | 13.79 | 2000 | 1.8067          | 0.8560 |
| 1.855         | 14.48 | 2100 | 1.8129          | 0.8177 |
| 1.5901        | 15.17 | 2200 | 1.7891          | 0.8367 |
| 1.4848        | 15.86 | 2300 | 1.7821          | 0.8201 |
| 1.8754        | 16.55 | 2400 | 1.7700          | 0.8137 |
| 1.7975        | 17.24 | 2500 | 1.7795          | 0.8171 |
| 1.5194        | 17.93 | 2600 | 1.7605          | 0.7977 |
| 1.4374        | 18.62 | 2700 | 1.7529          | 0.7978 |
| 1.7498        | 19.31 | 2800 | 1.7522          | 0.8023 |
| 1.7452        | 20.0  | 2900 | 1.7482          | 0.7987 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
