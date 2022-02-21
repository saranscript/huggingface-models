---
language:
- bas
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Basaa
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: bas
    metrics:
       - name: Test WER
         type: wer
         value: 104.08
       - name: Test CER
         type: cer
         value: 228.48
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-basaa

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - BAS dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5975
- Wer: 0.4981

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 200.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 2.9287        | 15.62  | 500  | 2.8774          | 1.0    |
| 1.1182        | 31.25  | 1000 | 0.6248          | 0.7131 |
| 0.8329        | 46.88  | 1500 | 0.5573          | 0.5792 |
| 0.7109        | 62.5   | 2000 | 0.5420          | 0.5683 |
| 0.6295        | 78.12  | 2500 | 0.5166          | 0.5395 |
| 0.5715        | 93.75  | 3000 | 0.5487          | 0.5629 |
| 0.5016        | 109.38 | 3500 | 0.5370          | 0.5471 |
| 0.4661        | 125.0  | 4000 | 0.5621          | 0.5395 |
| 0.423         | 140.62 | 4500 | 0.5658          | 0.5248 |
| 0.3793        | 156.25 | 5000 | 0.5921          | 0.4981 |
| 0.3651        | 171.88 | 5500 | 0.5987          | 0.4888 |
| 0.3351        | 187.5  | 6000 | 0.6017          | 0.4948 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
