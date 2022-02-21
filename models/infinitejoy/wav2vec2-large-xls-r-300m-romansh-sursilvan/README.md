---
language:
- rm-sursilv
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- rm-sursilv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Romansh Sursilvan
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: rm-sursilv
    metrics:
       - name: Test WER
         type: wer
         value: 19.816
       - name: Test CER
         type: cer
         value: 4.153
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-romansh-sursilvan

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - RM-SURSILV dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2163
- Wer: 0.1981

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
- num_epochs: 120.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| 1.1004        | 23.81  | 2000  | 0.3710          | 0.4191 |
| 0.7002        | 47.62  | 4000  | 0.2342          | 0.2562 |
| 0.5573        | 71.43  | 6000  | 0.2175          | 0.2177 |
| 0.4799        | 95.24  | 8000  | 0.2109          | 0.1987 |
| 0.4511        | 119.05 | 10000 | 0.2164          | 0.1975 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
