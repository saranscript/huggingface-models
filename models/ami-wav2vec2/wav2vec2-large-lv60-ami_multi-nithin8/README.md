---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-large-lv60-ami_multi-nithin8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-lv60-ami_multi-nithin8

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4945
- Wer: 0.4291

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
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 40.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.336         | 2.16  | 2500  | 1.2807          | 0.4097 |
| 1.216         | 4.31  | 5000  | 1.2406          | 0.3931 |
| 1.1353        | 6.47  | 7500  | 1.2145          | 0.3801 |
| 1.0674        | 8.62  | 10000 | 1.1930          | 0.3825 |
| 1.0223        | 10.78 | 12500 | 1.2283          | 0.3907 |
| 1.009         | 12.93 | 15000 | 1.2266          | 0.3810 |
| 0.8998        | 15.09 | 17500 | 1.2719          | 0.3839 |
| 0.8912        | 17.24 | 20000 | 1.2889          | 0.3867 |
| 0.8459        | 19.4  | 22500 | 1.3031          | 0.3941 |
| 0.8193        | 21.55 | 25000 | 1.3543          | 0.3862 |
| 0.8048        | 23.71 | 27500 | 1.3533          | 0.3858 |
| 0.7663        | 25.86 | 30000 | 1.3941          | 0.3993 |
| 0.7311        | 28.02 | 32500 | 1.4745          | 0.3937 |
| 0.716         | 30.17 | 35000 | 1.4788          | 0.3989 |
| 0.6868        | 32.33 | 37500 | 1.4966          | 0.3925 |
| 0.6558        | 34.48 | 40000 | 1.5457          | 0.3901 |
| 0.6473        | 36.64 | 42500 | 1.5662          | 0.3944 |
| 0.631         | 38.79 | 45000 | 1.5689          | 0.3956 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
