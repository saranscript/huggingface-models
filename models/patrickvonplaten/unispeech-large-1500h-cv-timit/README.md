---
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: unispeech-large-1500h-cv-timit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# unispeech-large-1500h-cv-timit

This model is a fine-tuned version of [microsoft/unispeech-large-1500h-cv](https://huggingface.co/microsoft/unispeech-large-1500h-cv) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3099
- Wer: 0.2196

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
| 4.64          | 0.69  | 100  | 3.9717          | 0.9981 |
| 2.6793        | 1.38  | 200  | 2.6264          | 1.0    |
| 1.2221        | 2.07  | 300  | 0.9999          | 0.7167 |
| 0.9009        | 2.76  | 400  | 0.6509          | 0.5570 |
| 0.4352        | 3.45  | 500  | 0.4682          | 0.4332 |
| 0.227         | 4.14  | 600  | 0.3661          | 0.3565 |
| 0.2169        | 4.83  | 700  | 0.3244          | 0.3203 |
| 0.2687        | 5.52  | 800  | 0.3137          | 0.2981 |
| 0.127         | 6.21  | 900  | 0.3220          | 0.2828 |
| 0.0922        | 6.9   | 1000 | 0.3075          | 0.2708 |
| 0.0965        | 7.59  | 1100 | 0.2779          | 0.2576 |
| 0.1298        | 8.28  | 1200 | 0.3111          | 0.2480 |
| 0.0855        | 8.97  | 1300 | 0.3021          | 0.2421 |
| 0.0629        | 9.66  | 1400 | 0.3122          | 0.2511 |
| 0.0471        | 10.34 | 1500 | 0.2965          | 0.2368 |
| 0.0871        | 11.03 | 1600 | 0.3247          | 0.2387 |
| 0.0503        | 11.72 | 1700 | 0.3359          | 0.2363 |
| 0.0402        | 12.41 | 1800 | 0.2976          | 0.2332 |
| 0.0336        | 13.1  | 1900 | 0.3139          | 0.2321 |
| 0.0634        | 13.79 | 2000 | 0.3188          | 0.2309 |
| 0.0429        | 14.48 | 2100 | 0.3145          | 0.2335 |
| 0.028         | 15.17 | 2200 | 0.3244          | 0.2242 |
| 0.0255        | 15.86 | 2300 | 0.2914          | 0.2196 |
| 0.0406        | 16.55 | 2400 | 0.3249          | 0.2202 |
| 0.0512        | 17.24 | 2500 | 0.3037          | 0.2198 |
| 0.0269        | 17.93 | 2600 | 0.3218          | 0.2242 |
| 0.0287        | 18.62 | 2700 | 0.3106          | 0.2185 |
| 0.0319        | 19.31 | 2800 | 0.3124          | 0.2217 |
| 0.0494        | 20.0  | 2900 | 0.3099          | 0.2196 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
