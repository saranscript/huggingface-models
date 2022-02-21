---
language:
- ha
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- ha
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Hausa
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: ha
    metrics:
       - name: Test WER
         type: wer
         value: 100
       - name: Test CER
         type: cer
         value: 132.32
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-hausa

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - HA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5756
- Wer: 0.6014

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
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.7064        | 11.36 | 500  | 2.7112          | 1.0    |
| 1.3079        | 22.73 | 1000 | 0.7337          | 0.7776 |
| 1.0919        | 34.09 | 1500 | 0.5938          | 0.7023 |
| 0.9546        | 45.45 | 2000 | 0.5698          | 0.6133 |
| 0.8895        | 56.82 | 2500 | 0.5739          | 0.6142 |
| 0.8152        | 68.18 | 3000 | 0.5579          | 0.6091 |
| 0.7703        | 79.55 | 3500 | 0.5813          | 0.6210 |
| 0.732         | 90.91 | 4000 | 0.5756          | 0.5860 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
