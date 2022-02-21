---
language:
- sv-SE
license: cc0-1.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- sv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Swedish
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: mozilla-foundation/common_voice_8_0
      type: mozilla-foundation/common_voice_8_0
      args: sv-SE
    metrics:
       - name: Test WER
         type: wer
         value: 8.72
       - name: Test CER
         type: cer
         value: 3.05
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: speech-recognition-community-v2/dev_data
      type: speech-recognition-community-v2/dev_data
      args: sv
    metrics:
       - name: Test WER
         type: wer
         value: 19.67
       - name: Test CER
         type: cer
         value: 8.94
---

# 

This model is a fine-tuned version of [KBLab/wav2vec2-large-voxrex](https://huggingface.co/KBLab/wav2vec2-large-voxrex) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SV-SE dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1595
- Wer: 0.1200

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.00025
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.25
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.0418        | 5.49  | 500  | 3.0176          | 1.0    |
| 1.1819        | 10.98 | 1000 | 0.2562          | 0.2168 |
| 1.0032        | 16.48 | 1500 | 0.1746          | 0.1546 |
| 0.9077        | 21.97 | 2000 | 0.1600          | 0.1339 |
| 0.8687        | 27.47 | 2500 | 0.1647          | 0.1378 |
| 0.8081        | 32.96 | 3000 | 0.1608          | 0.1353 |
| 0.7923        | 38.46 | 3500 | 0.1534          | 0.1277 |
| 0.7349        | 43.95 | 4000 | 0.1546          | 0.1303 |
| 0.7199        | 49.45 | 4500 | 0.1617          | 0.1277 |
| 0.7028        | 54.94 | 5000 | 0.1572          | 0.1287 |
| 0.6912        | 60.44 | 5500 | 0.1560          | 0.1249 |
| 0.6492        | 65.93 | 6000 | 0.1542          | 0.1260 |
| 0.6407        | 71.43 | 6500 | 0.1605          | 0.1240 |
| 0.6222        | 76.92 | 7000 | 0.1577          | 0.1219 |
| 0.6039        | 82.42 | 7500 | 0.1645          | 0.1249 |
| 0.5928        | 87.91 | 8000 | 0.1590          | 0.1214 |
| 0.6022        | 93.4  | 8500 | 0.1597          | 0.1213 |
| 0.5814        | 98.9  | 9000 | 0.1599          | 0.1199 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
