---
language:
- lt
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- lt
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Lithuanian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: lt
    metrics:
       - name: Test WER
         type: wer
         value: 24.859
       - name: Test CER
         type: cer
         value: 4.764
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-lithuanian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - LT dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1722
- Wer: 0.2486

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
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.6837        | 8.0   | 2000  | 0.6649          | 0.7515 |
| 1.1105        | 16.0  | 4000  | 0.2386          | 0.3436 |
| 1.0069        | 24.0  | 6000  | 0.2008          | 0.2968 |
| 0.9417        | 32.0  | 8000  | 0.1915          | 0.2774 |
| 0.887         | 40.0  | 10000 | 0.1819          | 0.2616 |
| 0.8563        | 48.0  | 12000 | 0.1729          | 0.2475 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
