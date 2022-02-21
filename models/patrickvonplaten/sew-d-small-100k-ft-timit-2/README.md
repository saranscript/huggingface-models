---
license: apache-2.0
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: sew-d-small-100k-ft-timit-2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-d-small-100k-ft-timit-2

This model is a fine-tuned version of [asapp/sew-d-small-100k](https://huggingface.co/asapp/sew-d-small-100k) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 1.7357
- Wer: 0.7935

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
| 4.1554        | 0.69  | 100  | 4.0531          | 1.0    |
| 2.9584        | 1.38  | 200  | 2.9775          | 1.0    |
| 2.9355        | 2.07  | 300  | 2.9412          | 1.0    |
| 2.9048        | 2.76  | 400  | 2.9143          | 1.0    |
| 2.8568        | 3.45  | 500  | 2.8786          | 1.0    |
| 2.7248        | 4.14  | 600  | 2.7553          | 0.9833 |
| 2.6124        | 4.83  | 700  | 2.5874          | 1.0511 |
| 2.5463        | 5.52  | 800  | 2.4630          | 1.0883 |
| 2.3302        | 6.21  | 900  | 2.3948          | 1.0651 |
| 2.0669        | 6.9   | 1000 | 2.2228          | 0.9920 |
| 2.1991        | 7.59  | 1100 | 2.0815          | 0.9185 |
| 2.293         | 8.28  | 1200 | 2.0229          | 0.8674 |
| 2.0366        | 8.97  | 1300 | 1.9590          | 0.9165 |
| 1.767         | 9.66  | 1400 | 1.9129          | 0.8125 |
| 1.6222        | 10.34 | 1500 | 1.8868          | 0.8259 |
| 2.173         | 11.03 | 1600 | 1.8691          | 0.8661 |
| 1.8614        | 11.72 | 1700 | 1.8388          | 0.8250 |
| 1.5928        | 12.41 | 1800 | 1.8528          | 0.7772 |
| 1.5978        | 13.1  | 1900 | 1.8002          | 0.7892 |
| 1.9886        | 13.79 | 2000 | 1.7848          | 0.8448 |
| 1.8042        | 14.48 | 2100 | 1.7819          | 0.8156 |
| 1.5488        | 15.17 | 2200 | 1.7615          | 0.8228 |
| 1.4468        | 15.86 | 2300 | 1.7565          | 0.7946 |
| 1.8153        | 16.55 | 2400 | 1.7537          | 0.8341 |
| 1.77          | 17.24 | 2500 | 1.7527          | 0.7958 |
| 1.4742        | 17.93 | 2600 | 1.7592          | 0.7850 |
| 1.4088        | 18.62 | 2700 | 1.7421          | 0.8149 |
| 1.7066        | 19.31 | 2800 | 1.7382          | 0.7977 |
| 1.7068        | 20.0  | 2900 | 1.7357          | 0.7935 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
