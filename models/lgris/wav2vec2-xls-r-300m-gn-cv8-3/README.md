---
language:
- gn
license: apache-2.0
tags:
- automatic-speech-recognition
- generated_from_trainer
- gn
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-xls-r-300m-gn-cv8-3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-gn-cv8-3

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9517
- Wer: 0.8542

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- training_steps: 5000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 19.9125       | 5.54   | 100  | 5.4279          | 1.0    |
| 3.8031        | 11.11  | 200  | 3.3070          | 1.0    |
| 3.3783        | 16.65  | 300  | 3.2450          | 1.0    |
| 3.3472        | 22.22  | 400  | 3.2424          | 1.0    |
| 3.2714        | 27.76  | 500  | 3.1100          | 1.0    |
| 3.2367        | 33.32  | 600  | 3.1091          | 1.0    |
| 3.1968        | 38.86  | 700  | 3.1013          | 1.0    |
| 3.2004        | 44.43  | 800  | 3.1173          | 1.0    |
| 3.1656        | 49.97  | 900  | 3.0682          | 1.0    |
| 3.1563        | 55.54  | 1000 | 3.0457          | 1.0    |
| 3.1356        | 61.11  | 1100 | 3.0139          | 1.0    |
| 3.086         | 66.65  | 1200 | 2.8108          | 1.0    |
| 2.954         | 72.22  | 1300 | 2.3238          | 1.0    |
| 2.6125        | 77.76  | 1400 | 1.6461          | 1.0    |
| 2.3296        | 83.32  | 1500 | 1.2834          | 0.9744 |
| 2.1345        | 88.86  | 1600 | 1.1091          | 0.9693 |
| 2.0346        | 94.43  | 1700 | 1.0273          | 0.9233 |
| 1.9611        | 99.97  | 1800 | 0.9642          | 0.9182 |
| 1.9066        | 105.54 | 1900 | 0.9590          | 0.9105 |
| 1.8178        | 111.11 | 2000 | 0.9679          | 0.9028 |
| 1.7799        | 116.65 | 2100 | 0.9007          | 0.8619 |
| 1.7726        | 122.22 | 2200 | 0.9689          | 0.8951 |
| 1.7389        | 127.76 | 2300 | 0.8876          | 0.8593 |
| 1.7151        | 133.32 | 2400 | 0.8716          | 0.8542 |
| 1.6842        | 138.86 | 2500 | 0.9536          | 0.8772 |
| 1.6449        | 144.43 | 2600 | 0.9296          | 0.8542 |
| 1.5978        | 149.97 | 2700 | 0.8895          | 0.8440 |
| 1.6515        | 155.54 | 2800 | 0.9162          | 0.8568 |
| 1.6586        | 161.11 | 2900 | 0.9039          | 0.8568 |
| 1.5966        | 166.65 | 3000 | 0.8627          | 0.8542 |
| 1.5695        | 172.22 | 3100 | 0.9549          | 0.8824 |
| 1.5699        | 177.76 | 3200 | 0.9332          | 0.8517 |
| 1.5297        | 183.32 | 3300 | 0.9163          | 0.8338 |
| 1.5367        | 188.86 | 3400 | 0.8822          | 0.8312 |
| 1.5586        | 194.43 | 3500 | 0.9217          | 0.8363 |
| 1.5429        | 199.97 | 3600 | 0.9564          | 0.8568 |
| 1.5273        | 205.54 | 3700 | 0.9508          | 0.8542 |
| 1.5043        | 211.11 | 3800 | 0.9374          | 0.8542 |
| 1.4724        | 216.65 | 3900 | 0.9622          | 0.8619 |
| 1.4794        | 222.22 | 4000 | 0.9550          | 0.8363 |
| 1.4843        | 227.76 | 4100 | 0.9577          | 0.8465 |
| 1.4781        | 233.32 | 4200 | 0.9543          | 0.8440 |
| 1.4507        | 238.86 | 4300 | 0.9553          | 0.8491 |
| 1.4997        | 244.43 | 4400 | 0.9728          | 0.8491 |
| 1.4371        | 249.97 | 4500 | 0.9543          | 0.8670 |
| 1.4825        | 255.54 | 4600 | 0.9636          | 0.8619 |
| 1.4187        | 261.11 | 4700 | 0.9609          | 0.8440 |
| 1.4363        | 266.65 | 4800 | 0.9567          | 0.8593 |
| 1.4463        | 272.22 | 4900 | 0.9581          | 0.8542 |
| 1.4117        | 277.76 | 5000 | 0.9517          | 0.8542 |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.11.0
