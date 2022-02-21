---
license: apache-2.0
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: wav2vec2-base-timit-fine-tuned
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-timit-fine-tuned

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3457
- Wer: 0.2151

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
| 3.1621        | 0.69  | 100  | 3.1102          | 1.0    |
| 2.9592        | 1.38  | 200  | 2.9603          | 1.0    |
| 2.9116        | 2.07  | 300  | 2.8921          | 1.0    |
| 2.1332        | 2.76  | 400  | 1.9718          | 0.9958 |
| 0.8477        | 3.45  | 500  | 0.7813          | 0.5237 |
| 0.4251        | 4.14  | 600  | 0.5166          | 0.3982 |
| 0.3743        | 4.83  | 700  | 0.4400          | 0.3578 |
| 0.4194        | 5.52  | 800  | 0.4077          | 0.3370 |
| 0.23          | 6.21  | 900  | 0.4018          | 0.3142 |
| 0.1554        | 6.9   | 1000 | 0.3623          | 0.2995 |
| 0.1511        | 7.59  | 1100 | 0.3433          | 0.2697 |
| 0.1983        | 8.28  | 1200 | 0.3539          | 0.2715 |
| 0.1443        | 8.97  | 1300 | 0.3622          | 0.2551 |
| 0.0971        | 9.66  | 1400 | 0.3580          | 0.2519 |
| 0.0764        | 10.34 | 1500 | 0.3529          | 0.2437 |
| 0.1203        | 11.03 | 1600 | 0.3455          | 0.2431 |
| 0.0881        | 11.72 | 1700 | 0.3648          | 0.2415 |
| 0.0521        | 12.41 | 1800 | 0.3564          | 0.2320 |
| 0.0434        | 13.1  | 1900 | 0.3485          | 0.2270 |
| 0.0864        | 13.79 | 2000 | 0.3517          | 0.2228 |
| 0.0651        | 14.48 | 2100 | 0.3506          | 0.2285 |
| 0.0423        | 15.17 | 2200 | 0.3428          | 0.2247 |
| 0.0302        | 15.86 | 2300 | 0.3372          | 0.2198 |
| 0.0548        | 16.55 | 2400 | 0.3496          | 0.2196 |
| 0.0674        | 17.24 | 2500 | 0.3407          | 0.2166 |
| 0.0291        | 17.93 | 2600 | 0.3512          | 0.2171 |
| 0.0298        | 18.62 | 2700 | 0.3363          | 0.2158 |
| 0.0419        | 19.31 | 2800 | 0.3493          | 0.2145 |
| 0.046         | 20.0  | 2900 | 0.3457          | 0.2151 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
