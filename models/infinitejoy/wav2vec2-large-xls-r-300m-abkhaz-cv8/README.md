---
language:
- ab
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- ab
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Abkhaz
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: ab
    metrics:
       - name: Test WER
         type: wer
         value: 27.600
       - name: Test CER
         type: cer
         value: 4.577
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-abkhaz-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - AB dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1614
- Wer: 0.2907

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 4000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.2881        | 4.26  | 4000  | 0.3764          | 0.6461 |
| 1.0767        | 8.53  | 8000  | 0.2657          | 0.5164 |
| 0.9841        | 12.79 | 12000 | 0.2330          | 0.4445 |
| 0.9274        | 17.06 | 16000 | 0.2134          | 0.3929 |
| 0.8781        | 21.32 | 20000 | 0.1945          | 0.3886 |
| 0.8381        | 25.59 | 24000 | 0.1840          | 0.3737 |
| 0.8054        | 29.85 | 28000 | 0.1756          | 0.3523 |
| 0.7763        | 34.12 | 32000 | 0.1745          | 0.3299 |
| 0.7474        | 38.38 | 36000 | 0.1677          | 0.3074 |
| 0.7298        | 42.64 | 40000 | 0.1649          | 0.2963 |
| 0.7125        | 46.91 | 44000 | 0.1617          | 0.2931 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
