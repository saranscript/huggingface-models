---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xlsr-hindi-demo-colab_2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-hindi-demo-colab_2

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 3.8793
- Wer: 1.1357

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 20
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 22.381        | 1.11  | 20   | 22.1964         | 1.0    |
| 7.6212        | 2.22  | 40   | 4.0591          | 1.0    |
| 3.6951        | 3.32  | 60   | 3.6782          | 1.0    |
| 3.5574        | 4.43  | 80   | 3.6776          | 1.0    |
| 3.5374        | 5.54  | 100  | 3.5649          | 1.0    |
| 3.5512        | 6.65  | 120  | 3.5266          | 1.0    |
| 3.5075        | 7.76  | 140  | 3.6860          | 1.0    |
| 3.5097        | 8.86  | 160  | 3.4941          | 1.0    |
| 3.481         | 9.97  | 180  | 3.4659          | 1.0    |
| 3.5623        | 11.11 | 200  | 3.7254          | 1.0    |
| 3.4404        | 12.22 | 220  | 3.5225          | 1.0    |
| 3.432         | 13.32 | 240  | 3.5706          | 1.0    |
| 3.4177        | 14.43 | 260  | 3.3833          | 1.0    |
| 3.3735        | 15.54 | 280  | 3.4140          | 1.0    |
| 3.31          | 16.65 | 300  | 3.2702          | 1.0    |
| 3.2256        | 17.76 | 320  | 3.2405          | 1.0    |
| 3.0546        | 18.86 | 340  | 3.1644          | 1.0    |
| 2.7233        | 19.97 | 360  | 2.9753          | 1.0    |
| 2.2822        | 21.11 | 380  | 3.1119          | 1.1183 |
| 1.8027        | 22.22 | 400  | 3.0035          | 1.2378 |
| 1.5274        | 23.32 | 420  | 2.8536          | 1.2227 |
| 1.2313        | 24.43 | 440  | 2.9544          | 1.0951 |
| 1.0956        | 25.54 | 460  | 2.8814          | 1.0661 |
| 0.9456        | 26.65 | 480  | 3.1192          | 1.1589 |
| 0.7893        | 27.76 | 500  | 3.2919          | 1.1833 |
| 0.7256        | 28.86 | 520  | 3.0864          | 1.0951 |
| 0.6051        | 29.97 | 540  | 3.5888          | 1.1821 |
| 0.6087        | 31.11 | 560  | 3.4579          | 1.1392 |
| 0.5529        | 32.22 | 580  | 3.1998          | 1.0708 |
| 0.5211        | 33.32 | 600  | 3.4655          | 1.1311 |
| 0.4506        | 34.43 | 620  | 3.4338          | 1.1694 |
| 0.4101        | 35.54 | 640  | 3.5189          | 1.1450 |
| 0.4484        | 36.65 | 660  | 3.6585          | 1.1601 |
| 0.4038        | 37.76 | 680  | 3.6314          | 1.1497 |
| 0.3539        | 38.86 | 700  | 3.6955          | 1.1485 |
| 0.3898        | 39.97 | 720  | 3.5738          | 1.1148 |
| 0.35          | 41.11 | 740  | 3.6594          | 1.1195 |
| 0.3328        | 42.22 | 760  | 3.6894          | 1.1299 |
| 0.3264        | 43.32 | 780  | 3.7290          | 1.1021 |
| 0.3364        | 44.43 | 800  | 3.7256          | 1.1543 |
| 0.3071        | 45.54 | 820  | 3.8834          | 1.1415 |
| 0.3074        | 46.65 | 840  | 3.8077          | 1.1450 |
| 0.3064        | 47.76 | 860  | 3.8733          | 1.1346 |
| 0.3223        | 48.86 | 880  | 3.8780          | 1.1323 |
| 0.275         | 49.97 | 900  | 3.8793          | 1.1357 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
