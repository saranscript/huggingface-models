---
license: apache-2.0
tags:
- automatic-speech-recognition
- librispeech_asr
- generated_from_trainer
model-index:
- name: sew-mid-100k-librispeech-clean-100h-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-mid-100k-librispeech-clean-100h-ft

This model is a fine-tuned version of [asapp/sew-mid-100k](https://huggingface.co/asapp/sew-mid-100k) on the LIBRISPEECH_ASR - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1976
- Wer: 0.1665

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 32
- total_eval_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.4274        | 0.11  | 100  | 4.1419          | 1.0    |
| 2.9657        | 0.22  | 200  | 3.1203          | 1.0    |
| 2.9069        | 0.34  | 300  | 3.0107          | 1.0    |
| 2.8666        | 0.45  | 400  | 2.8960          | 1.0    |
| 1.4535        | 0.56  | 500  | 1.4062          | 0.8664 |
| 0.6821        | 0.67  | 600  | 0.5530          | 0.4930 |
| 0.4827        | 0.78  | 700  | 0.4122          | 0.3630 |
| 0.4485        | 0.9   | 800  | 0.3597          | 0.3243 |
| 0.2666        | 1.01  | 900  | 0.3104          | 0.2790 |
| 0.2378        | 1.12  | 1000 | 0.2913          | 0.2613 |
| 0.2516        | 1.23  | 1100 | 0.2702          | 0.2452 |
| 0.2456        | 1.35  | 1200 | 0.2619          | 0.2338 |
| 0.2392        | 1.46  | 1300 | 0.2466          | 0.2195 |
| 0.2117        | 1.57  | 1400 | 0.2379          | 0.2092 |
| 0.1837        | 1.68  | 1500 | 0.2295          | 0.2029 |
| 0.1757        | 1.79  | 1600 | 0.2240          | 0.1949 |
| 0.1626        | 1.91  | 1700 | 0.2195          | 0.1927 |
| 0.168         | 2.02  | 1800 | 0.2137          | 0.1853 |
| 0.168         | 2.13  | 1900 | 0.2123          | 0.1839 |
| 0.1576        | 2.24  | 2000 | 0.2095          | 0.1803 |
| 0.1756        | 2.35  | 2100 | 0.2075          | 0.1776 |
| 0.1467        | 2.47  | 2200 | 0.2049          | 0.1754 |
| 0.1702        | 2.58  | 2300 | 0.2013          | 0.1722 |
| 0.177         | 2.69  | 2400 | 0.1993          | 0.1701 |
| 0.1417        | 2.8   | 2500 | 0.1983          | 0.1688 |
| 0.1302        | 2.91  | 2600 | 0.1977          | 0.1678 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.13.4.dev0
- Tokenizers 0.10.3
