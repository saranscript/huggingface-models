---
language:
- rm-vallader
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- rm-vallader
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Romansh Vallader
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: rm-vallader
    metrics:
       - name: Test WER
         type: wer
         value: 31.689
       - name: Test CER
         type: cer
         value: 7.202
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-romansh-vallader

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - RM-VALLADER dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3155
- Wer: 0.3162

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
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9556        | 15.62 | 500  | 2.9300          | 1.0    |
| 1.7874        | 31.25 | 1000 | 0.7566          | 0.6509 |
| 1.0131        | 46.88 | 1500 | 0.3671          | 0.3828 |
| 0.8439        | 62.5  | 2000 | 0.3350          | 0.3416 |
| 0.7502        | 78.12 | 2500 | 0.3155          | 0.3296 |
| 0.7093        | 93.75 | 3000 | 0.3182          | 0.3186 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
