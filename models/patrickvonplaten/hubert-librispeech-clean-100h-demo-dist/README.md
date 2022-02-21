---
license: apache-2.0
tags:
- speech-recognition
- librispeech_asr
- generated_from_trainer
model-index:
- name: hubert-librispeech-clean-100h-demo-dist
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hubert-librispeech-clean-100h-demo-dist

This model is a fine-tuned version of [facebook/hubert-large-ll60k](https://huggingface.co/facebook/hubert-large-ll60k) on the LIBRISPEECH_ASR - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0984
- Wer: 0.0883

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
| 2.9031        | 0.11  | 100  | 2.9220          | 1.0    |
| 2.6437        | 0.22  | 200  | 2.6268          | 1.0    |
| 0.3934        | 0.34  | 300  | 0.4860          | 0.4182 |
| 0.3531        | 0.45  | 400  | 0.3088          | 0.2894 |
| 0.2255        | 0.56  | 500  | 0.2568          | 0.2426 |
| 0.3379        | 0.67  | 600  | 0.2073          | 0.2011 |
| 0.2419        | 0.78  | 700  | 0.1849          | 0.1838 |
| 0.2128        | 0.9   | 800  | 0.1662          | 0.1690 |
| 0.1341        | 1.01  | 900  | 0.1600          | 0.1541 |
| 0.0946        | 1.12  | 1000 | 0.1431          | 0.1404 |
| 0.1643        | 1.23  | 1100 | 0.1373          | 0.1304 |
| 0.0663        | 1.35  | 1200 | 0.1293          | 0.1307 |
| 0.162         | 1.46  | 1300 | 0.1247          | 0.1266 |
| 0.1433        | 1.57  | 1400 | 0.1246          | 0.1262 |
| 0.1581        | 1.68  | 1500 | 0.1219          | 0.1154 |
| 0.1036        | 1.79  | 1600 | 0.1127          | 0.1081 |
| 0.1352        | 1.91  | 1700 | 0.1087          | 0.1040 |
| 0.0471        | 2.02  | 1800 | 0.1085          | 0.1005 |
| 0.0945        | 2.13  | 1900 | 0.1066          | 0.0973 |
| 0.0843        | 2.24  | 2000 | 0.1102          | 0.0964 |
| 0.0774        | 2.35  | 2100 | 0.1079          | 0.0940 |
| 0.0952        | 2.47  | 2200 | 0.1056          | 0.0927 |
| 0.0635        | 2.58  | 2300 | 0.1026          | 0.0920 |
| 0.0665        | 2.69  | 2400 | 0.1012          | 0.0905 |
| 0.034         | 2.8   | 2500 | 0.1009          | 0.0900 |
| 0.0251        | 2.91  | 2600 | 0.0993          | 0.0883 |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
