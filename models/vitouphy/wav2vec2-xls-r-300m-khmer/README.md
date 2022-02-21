---
language:
- km
license: apache-2.0
tags:
- automatic-speech-recognition
- openslr
- robust-speech-event
- km
- generated_from_trainer
model-index:
- name: xls-r-300m-km
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: OpenSLR km
      type: openslr
      args: km
    metrics:
       - name: Test WER
         type: wer
         value: 25.70
       - name: Test CER
         type: cer
         value: 7.03
  - task:
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: km
    metrics:
       - name: Test WER
         type: wer
         value: 25.70
       - name: Test CER
         type: cer
         value: 7.03
---

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the openslr dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3281
- Wer: 0.3462

# Evaluation results on OpenSLR "test" (self-split 10%) (Running ./eval.py):
- WER: 0.3216977389924633
- CER: 0.08653361193169537

# Evaluation results with language model on OpenSLR "test" (self-split 10%) (Running ./eval.py):
- WER: 0.257040856802856
- CER: 0.07025001801282513

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.0795        | 5.47  | 400  | 4.4121          | 1.0    |
| 3.5658        | 10.95 | 800  | 3.5203          | 1.0    |
| 3.3689        | 16.43 | 1200 | 2.8984          | 0.9996 |
| 2.01          | 21.91 | 1600 | 1.0041          | 0.7288 |
| 1.6783        | 27.39 | 2000 | 0.6941          | 0.5989 |
| 1.527         | 32.87 | 2400 | 0.5599          | 0.5282 |
| 1.4278        | 38.35 | 2800 | 0.4827          | 0.4806 |
| 1.3458        | 43.83 | 3200 | 0.4429          | 0.4532 |
| 1.2893        | 49.31 | 3600 | 0.4156          | 0.4330 |
| 1.2441        | 54.79 | 4000 | 0.4020          | 0.4040 |
| 1.188         | 60.27 | 4400 | 0.3777          | 0.3866 |
| 1.1628        | 65.75 | 4800 | 0.3607          | 0.3858 |
| 1.1324        | 71.23 | 5200 | 0.3534          | 0.3604 |
| 1.0969        | 76.71 | 5600 | 0.3428          | 0.3624 |
| 1.0897        | 82.19 | 6000 | 0.3387          | 0.3567 |
| 1.0625        | 87.66 | 6400 | 0.3339          | 0.3499 |
| 1.0601        | 93.15 | 6800 | 0.3288          | 0.3446 |
| 1.0474        | 98.62 | 7200 | 0.3281          | 0.3462 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
