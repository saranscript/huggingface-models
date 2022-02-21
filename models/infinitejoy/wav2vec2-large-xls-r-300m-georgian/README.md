---
language:
- ka
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- ka
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Georgian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: ka
    metrics:
       - name: Test WER
         type: wer
         value: 42.09
       - name: Test CER
         type: cer
         value: 8.01
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-georgian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - KA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3666
- Wer: 0.4211

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.8805        | 5.95  | 500  | 0.7547          | 0.8438 |
| 1.2123        | 11.9  | 1000 | 0.4732          | 0.6542 |
| 1.0822        | 17.86 | 1500 | 0.4027          | 0.5778 |
| 0.9938        | 23.81 | 2000 | 0.3847          | 0.5524 |
| 0.9383        | 29.76 | 2500 | 0.3845          | 0.5204 |
| 0.8932        | 35.71 | 3000 | 0.3833          | 0.5297 |
| 0.8495        | 41.67 | 3500 | 0.3759          | 0.5036 |
| 0.8201        | 47.62 | 4000 | 0.3616          | 0.4859 |
| 0.7794        | 53.57 | 4500 | 0.3874          | 0.4938 |
| 0.735         | 59.52 | 5000 | 0.3748          | 0.4782 |
| 0.7082        | 65.48 | 5500 | 0.3615          | 0.4675 |
| 0.669         | 71.43 | 6000 | 0.3797          | 0.4601 |
| 0.6457        | 77.38 | 6500 | 0.3812          | 0.4515 |
| 0.6098        | 83.33 | 7000 | 0.3660          | 0.4343 |
| 0.5874        | 89.29 | 7500 | 0.3640          | 0.4257 |
| 0.5627        | 95.24 | 8000 | 0.3661          | 0.4239 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
