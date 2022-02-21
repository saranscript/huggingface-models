---
language:
- sr
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- sr
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: wav2vec2-large-xls-r-300m-sr-v20
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sr
    metrics:
       - name: Test WER
         type: wer
         value: 0.3313112459169389
       - name: Test CER
         type: cer
         value: 0.11472902097902098
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: sl
    metrics:
       - name: Test WER
         type: wer
         value: 0.953810623556582
       - name: Test CER
         type: cer
         value: 0.8068880824888259
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-sr-v20

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6695
- Wer: 0.3355

### Evaluation Commands

1. To evaluate on mozilla-foundation/common_voice_8_0 with test split

python eval.py --model_id DrishtiSharma/wav2vec2-large-xls-r-300m-sr-v20 --dataset mozilla-foundation/common_voice_8_0 --config sr --split test --log_outputs

2. To evaluate on speech-recognition-community-v2/dev_data

python eval.py --model_id DrishtiSharma/wav2vec2-large-xls-r-300m-sr-v20 --dataset speech-recognition-community-v2/dev_data --config sr --split validation --chunk_length_s 10 --stride_length_s 1

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 800
- num_epochs: 200
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 8.2198        | 7.5   | 300  | 2.9960          | 1.0    |
| 2.0533        | 15.0  | 600  | 0.6508          | 0.6314 |
| 0.4176        | 22.5  | 900  | 0.5726          | 0.5170 |
| 0.2327        | 30.0  | 1200 | 0.5771          | 0.5296 |
| 0.1723        | 37.5  | 1500 | 0.5508          | 0.4377 |
| 0.1226        | 45.0  | 1800 | 0.6567          | 0.4363 |
| 0.1101        | 52.5  | 2100 | 0.5819          | 0.4452 |
| 0.0934        | 60.0  | 2400 | 0.6449          | 0.4354 |
| 0.0752        | 67.5  | 2700 | 0.5584          | 0.4162 |
| 0.0645        | 75.0  | 3000 | 0.6289          | 0.4162 |
| 0.0539        | 82.5  | 3300 | 0.6153          | 0.4232 |
| 0.0482        | 90.0  | 3600 | 0.6772          | 0.4811 |
| 0.0441        | 97.5  | 3900 | 0.6156          | 0.4582 |
| 0.0403        | 105.0 | 4200 | 0.6077          | 0.3971 |
| 0.0371        | 112.5 | 4500 | 0.7354          | 0.4148 |
| 0.0279        | 120.0 | 4800 | 0.6316          | 0.3598 |
| 0.0198        | 127.5 | 5100 | 0.6615          | 0.3626 |
| 0.0185        | 135.0 | 5400 | 0.6914          | 0.3658 |
| 0.0183        | 142.5 | 5700 | 0.7087          | 0.3742 |
| 0.0154        | 150.0 | 6000 | 0.6930          | 0.3542 |
| 0.0143        | 157.5 | 6300 | 0.6787          | 0.3383 |
| 0.0118        | 165.0 | 6600 | 0.6347          | 0.3476 |
| 0.0101        | 172.5 | 6900 | 0.6235          | 0.3434 |
| 0.0103        | 180.0 | 7200 | 0.6078          | 0.3434 |
| 0.0063        | 187.5 | 7500 | 0.6740          | 0.3411 |
| 0.0057        | 195.0 | 7800 | 0.6695          | 0.3355 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
