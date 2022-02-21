---
language:
- tr
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-phoneme-300m-tr
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Wav2vec2-xls-r-phoneme-300m-tr

This model is a fine-tuned version of [wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6380
- PER: 0.1664

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 2
- total_train_batch_size: 32
- total_eval_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 20.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | PER    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 13.6687       | 0.92  | 100  | 12.4567         | 1.0    |
| 3.4219        | 1.83  | 200  | 3.4704          | 1.0    |
| 3.1846        | 2.75  | 300  | 3.2281          | 0.9935 |
| 2.0076        | 3.67  | 400  | 1.7415          | 0.5222 |
| 1.0244        | 4.59  | 500  | 1.0290          | 0.3323 |
| 0.7095        | 5.5   | 600  | 0.8424          | 0.2859 |
| 0.619         | 6.42  | 700  | 0.7389          | 0.2232 |
| 0.3541        | 7.34  | 800  | 0.7049          | 0.2043 |
| 0.2946        | 8.26  | 900  | 0.7065          | 0.2153 |
| 0.2868        | 9.17  | 1000 | 0.6840          | 0.2115 |
| 0.2245        | 10.09 | 1100 | 0.6714          | 0.1952 |
| 0.1394        | 11.01 | 1200 | 0.6864          | 0.1954 |
| 0.1288        | 11.93 | 1300 | 0.6696          | 0.2017 |
| 0.1568        | 12.84 | 1400 | 0.6468          | 0.1843 |
| 0.1269        | 13.76 | 1500 | 0.6736          | 0.1965 |
| 0.1101        | 14.68 | 1600 | 0.6689          | 0.1915 |
| 0.1388        | 15.6  | 1700 | 0.6690          | 0.1782 |
| 0.0739        | 16.51 | 1800 | 0.6364          | 0.1734 |
| 0.0897        | 17.43 | 1900 | 0.6480          | 0.1748 |
| 0.0795        | 18.35 | 2000 | 0.6356          | 0.1695 |
| 0.0823        | 19.27 | 2100 | 0.6382          | 0.1685 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.8.1
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
