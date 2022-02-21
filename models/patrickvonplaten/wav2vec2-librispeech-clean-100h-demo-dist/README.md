---
license: apache-2.0
tags:
- speech-recognition
- librispeech_asr
- generated_from_trainer
model-index:
- name: wav2vec2-librispeech-clean-100h-demo-dist
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-librispeech-clean-100h-demo-dist

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) on the LIBRISPEECH_ASR - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0572
- Wer: 0.0417

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
| 3.399         | 0.11  | 100  | 3.6153          | 1.0    |
| 2.8892        | 0.22  | 200  | 2.8963          | 1.0    |
| 2.8284        | 0.34  | 300  | 2.8574          | 1.0    |
| 0.7347        | 0.45  | 400  | 0.6158          | 0.4850 |
| 0.1138        | 0.56  | 500  | 0.2038          | 0.1560 |
| 0.248         | 0.67  | 600  | 0.1274          | 0.1024 |
| 0.2586        | 0.78  | 700  | 0.1108          | 0.0876 |
| 0.0733        | 0.9   | 800  | 0.0936          | 0.0762 |
| 0.044         | 1.01  | 900  | 0.0834          | 0.0662 |
| 0.0393        | 1.12  | 1000 | 0.0792          | 0.0622 |
| 0.0941        | 1.23  | 1100 | 0.0769          | 0.0627 |
| 0.036         | 1.35  | 1200 | 0.0731          | 0.0603 |
| 0.0768        | 1.46  | 1300 | 0.0713          | 0.0559 |
| 0.0518        | 1.57  | 1400 | 0.0686          | 0.0537 |
| 0.0815        | 1.68  | 1500 | 0.0639          | 0.0515 |
| 0.0603        | 1.79  | 1600 | 0.0636          | 0.0500 |
| 0.056         | 1.91  | 1700 | 0.0609          | 0.0480 |
| 0.0265        | 2.02  | 1800 | 0.0621          | 0.0465 |
| 0.0496        | 2.13  | 1900 | 0.0607          | 0.0449 |
| 0.0436        | 2.24  | 2000 | 0.0591          | 0.0446 |
| 0.0421        | 2.35  | 2100 | 0.0590          | 0.0428 |
| 0.0641        | 2.47  | 2200 | 0.0603          | 0.0443 |
| 0.0466        | 2.58  | 2300 | 0.0580          | 0.0429 |
| 0.0132        | 2.69  | 2400 | 0.0574          | 0.0423 |
| 0.0073        | 2.8   | 2500 | 0.0586          | 0.0417 |
| 0.0021        | 2.91  | 2600 | 0.0574          | 0.0412 |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
