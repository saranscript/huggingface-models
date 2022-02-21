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
- name: hello_2b_3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hello_2b_3

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-2b](https://huggingface.co/facebook/wav2vec2-xls-r-2b) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5615
- Wer: 0.9808

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-06
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 2
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- total_eval_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.6389        | 0.92  | 100  | 3.6218          | 1.0    |
| 1.6676        | 1.85  | 200  | 3.2655          | 1.0    |
| 0.3067        | 2.77  | 300  | 3.2273          | 1.0    |
| 0.1924        | 3.7   | 400  | 3.0238          | 0.9999 |
| 0.1777        | 4.63  | 500  | 2.1606          | 0.9991 |
| 0.1481        | 5.55  | 600  | 1.8742          | 0.9982 |
| 0.1128        | 6.48  | 700  | 2.0114          | 0.9994 |
| 0.1806        | 7.4   | 800  | 1.9032          | 0.9984 |
| 0.0399        | 8.33  | 900  | 2.0556          | 0.9996 |
| 0.0729        | 9.26  | 1000 | 2.0515          | 0.9987 |
| 0.0847        | 10.18 | 1100 | 2.2121          | 0.9995 |
| 0.0777        | 11.11 | 1200 | 1.7002          | 0.9923 |
| 0.0476        | 12.04 | 1300 | 1.5262          | 0.9792 |
| 0.0518        | 12.96 | 1400 | 1.5990          | 0.9832 |
| 0.071         | 13.88 | 1500 | 1.6326          | 0.9875 |
| 0.0333        | 14.81 | 1600 | 1.5955          | 0.9870 |
| 0.0369        | 15.74 | 1700 | 1.5577          | 0.9832 |
| 0.0689        | 16.66 | 1800 | 1.5415          | 0.9839 |
| 0.0227        | 17.59 | 1900 | 1.5450          | 0.9878 |
| 0.0472        | 18.51 | 2000 | 1.5642          | 0.9846 |
| 0.0214        | 19.44 | 2100 | 1.6103          | 0.9846 |
| 0.0289        | 20.37 | 2200 | 1.6467          | 0.9898 |
| 0.0182        | 21.29 | 2300 | 1.5268          | 0.9780 |
| 0.0439        | 22.22 | 2400 | 1.6001          | 0.9818 |
| 0.06          | 23.15 | 2500 | 1.5481          | 0.9813 |
| 0.0351        | 24.07 | 2600 | 1.5672          | 0.9820 |
| 0.0198        | 24.99 | 2700 | 1.6303          | 0.9856 |
| 0.0328        | 25.92 | 2800 | 1.5958          | 0.9831 |
| 0.0245        | 26.85 | 2900 | 1.5745          | 0.9809 |
| 0.0885        | 27.77 | 3000 | 1.5455          | 0.9809 |
| 0.0224        | 28.7  | 3100 | 1.5378          | 0.9824 |
| 0.0223        | 29.63 | 3200 | 1.5642          | 0.9810 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
