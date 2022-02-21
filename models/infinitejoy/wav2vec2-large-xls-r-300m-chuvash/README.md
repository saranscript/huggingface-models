---
language:
- cv
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- cv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Chuvash
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: cv
    metrics:
       - name: Test WER
         type: wer
         value: 60.31
       - name: Test CER
         type: cer
         value: 15.08
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-chuvash

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - CV dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7651
- Wer: 0.6166

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
| 1.8032        | 8.77  | 500  | 0.8059          | 0.8352 |
| 1.2608        | 17.54 | 1000 | 0.5828          | 0.6769 |
| 1.1337        | 26.32 | 1500 | 0.6892          | 0.6908 |
| 1.0457        | 35.09 | 2000 | 0.7077          | 0.6781 |
| 0.97          | 43.86 | 2500 | 0.5993          | 0.6228 |
| 0.8767        | 52.63 | 3000 | 0.7213          | 0.6604 |
| 0.8223        | 61.4  | 3500 | 0.8161          | 0.6968 |
| 0.7441        | 70.18 | 4000 | 0.7057          | 0.6184 |
| 0.7011        | 78.95 | 4500 | 0.7027          | 0.6024 |
| 0.6542        | 87.72 | 5000 | 0.7092          | 0.5979 |
| 0.6081        | 96.49 | 5500 | 0.7917          | 0.6324 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
