---
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: wav2vec2-base-repro-timit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-repro-timit

This model is a fine-tuned version of [patrickvonplaten/wav2vec2-base-repro-960h-libri-85k-steps](https://huggingface.co/patrickvonplaten/wav2vec2-base-repro-960h-libri-85k-steps) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8562
- Wer: 0.5484

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
| 5.9793        | 0.69  | 100  | 5.4532          | 1.0    |
| 2.9066        | 1.38  | 200  | 2.9070          | 1.0    |
| 2.2562        | 2.07  | 300  | 2.0323          | 1.0    |
| 1.5273        | 2.76  | 400  | 1.1510          | 0.8001 |
| 1.1085        | 3.45  | 500  | 0.9521          | 0.7053 |
| 0.813         | 4.14  | 600  | 0.8617          | 0.6702 |
| 0.8434        | 4.83  | 700  | 0.8068          | 0.6393 |
| 0.9631        | 5.52  | 800  | 0.7863          | 0.6248 |
| 0.707         | 6.21  | 900  | 0.7476          | 0.5973 |
| 0.5568        | 6.9   | 1000 | 0.7350          | 0.5911 |
| 0.6171        | 7.59  | 1100 | 0.7171          | 0.5841 |
| 0.7011        | 8.28  | 1200 | 0.7318          | 0.5798 |
| 0.5546        | 8.97  | 1300 | 0.7447          | 0.5767 |
| 0.4278        | 9.66  | 1400 | 0.7481          | 0.5650 |
| 0.3576        | 10.34 | 1500 | 0.7443          | 0.5713 |
| 0.5506        | 11.03 | 1600 | 0.7574          | 0.5664 |
| 0.4127        | 11.72 | 1700 | 0.8043          | 0.5631 |
| 0.3251        | 12.41 | 1800 | 0.7738          | 0.5550 |
| 0.3119        | 13.1  | 1900 | 0.7829          | 0.5516 |
| 0.4371        | 13.79 | 2000 | 0.8025          | 0.5556 |
| 0.3772        | 14.48 | 2100 | 0.8451          | 0.5559 |
| 0.2942        | 15.17 | 2200 | 0.8300          | 0.5556 |
| 0.2503        | 15.86 | 2300 | 0.8417          | 0.5541 |
| 0.3671        | 16.55 | 2400 | 0.8568          | 0.5528 |
| 0.3867        | 17.24 | 2500 | 0.8521          | 0.5510 |
| 0.2614        | 17.93 | 2600 | 0.8479          | 0.5523 |
| 0.2441        | 18.62 | 2700 | 0.8558          | 0.5494 |
| 0.3059        | 19.31 | 2800 | 0.8553          | 0.5474 |
| 0.3734        | 20.0  | 2900 | 0.8562          | 0.5484 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
