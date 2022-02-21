---
language:
- pa-IN
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: xls-r-300m-pa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xls-r-300m-pa

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - PA-IN dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0443
- Wer: 0.5715

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
- num_epochs: 500.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| 4.6694        | 19.22  | 500   | 4.0455          | 1.0    |
| 3.3907        | 38.45  | 1000  | 3.2836          | 1.0    |
| 2.0866        | 57.67  | 1500  | 1.2788          | 0.7715 |
| 1.4106        | 76.9   | 2000  | 0.7866          | 0.6891 |
| 1.1711        | 96.15  | 2500  | 0.6556          | 0.6272 |
| 1.038         | 115.37 | 3000  | 0.6195          | 0.5680 |
| 0.8989        | 134.6  | 3500  | 0.6563          | 0.5602 |
| 0.8021        | 153.82 | 4000  | 0.6644          | 0.5327 |
| 0.7161        | 173.07 | 4500  | 0.6844          | 0.5253 |
| 0.6449        | 192.3  | 5000  | 0.7018          | 0.5331 |
| 0.5659        | 211.52 | 5500  | 0.7451          | 0.5465 |
| 0.5118        | 230.75 | 6000  | 0.7857          | 0.5386 |
| 0.4385        | 249.97 | 6500  | 0.8062          | 0.5382 |
| 0.3984        | 269.22 | 7000  | 0.8316          | 0.5621 |
| 0.3666        | 288.45 | 7500  | 0.8736          | 0.5504 |
| 0.3256        | 307.67 | 8000  | 0.9133          | 0.5688 |
| 0.289         | 326.9  | 8500  | 0.9556          | 0.5684 |
| 0.2663        | 346.15 | 9000  | 0.9344          | 0.5708 |
| 0.2445        | 365.37 | 9500  | 0.9472          | 0.5590 |
| 0.2289        | 384.6  | 10000 | 0.9713          | 0.5672 |
| 0.2048        | 403.82 | 10500 | 0.9978          | 0.5762 |
| 0.1857        | 423.07 | 11000 | 1.0230          | 0.5798 |
| 0.1751        | 442.3  | 11500 | 1.0409          | 0.5755 |
| 0.1688        | 461.52 | 12000 | 1.0445          | 0.5727 |
| 0.1633        | 480.75 | 12500 | 1.0484          | 0.5739 |
| 0.1488        | 499.97 | 13000 | 1.0443          | 0.5715 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
