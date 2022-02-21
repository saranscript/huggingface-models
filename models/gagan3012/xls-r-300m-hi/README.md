---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: xls-r-300m-hi
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xls-r-300m-hi

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7522
- Wer: 1.0091

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.0417        | 2.59  | 500  | 5.1484          | 1.0    |
| 3.3722        | 5.18  | 1000 | 3.3380          | 1.0001 |
| 1.9752        | 7.77  | 1500 | 1.3910          | 1.0074 |
| 1.5868        | 10.36 | 2000 | 1.0298          | 1.0084 |
| 1.4413        | 12.95 | 2500 | 0.9313          | 1.0175 |
| 1.3296        | 15.54 | 3000 | 0.8966          | 1.0194 |
| 1.2746        | 18.13 | 3500 | 0.8875          | 1.0097 |
| 1.2147        | 20.73 | 4000 | 0.8746          | 1.0089 |
| 1.1774        | 23.32 | 4500 | 0.8383          | 1.0198 |
| 1.129         | 25.91 | 5000 | 0.7848          | 1.0167 |
| 1.0995        | 28.5  | 5500 | 0.7992          | 1.0210 |
| 1.0665        | 31.09 | 6000 | 0.7878          | 1.0107 |
| 1.0321        | 33.68 | 6500 | 0.7653          | 1.0082 |
| 1.0068        | 36.27 | 7000 | 0.7635          | 1.0065 |
| 0.9916        | 38.86 | 7500 | 0.7728          | 1.0090 |
| 0.9735        | 41.45 | 8000 | 0.7688          | 1.0070 |
| 0.9745        | 44.04 | 8500 | 0.7455          | 1.0097 |
| 0.9677        | 46.63 | 9000 | 0.7605          | 1.0099 |
| 0.9313        | 49.22 | 9500 | 0.7527          | 1.0097 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
