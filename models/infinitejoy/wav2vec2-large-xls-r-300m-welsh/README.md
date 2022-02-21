---
language:
- cy
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- cy
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Welsh
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: cy
    metrics:
       - name: Test WER
         type: wer
         value: 31.003
       - name: Test CER
         type: cer
         value: 7.775
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-welsh

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - CY dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2650
- Wer: 0.2702

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
- lr_scheduler_warmup_steps: 3000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.3454        | 8.2   | 3000  | 0.4926          | 0.5703 |
| 1.1202        | 16.39 | 6000  | 0.3529          | 0.3944 |
| 1.0058        | 24.59 | 9000  | 0.3143          | 0.3341 |
| 0.9287        | 32.79 | 12000 | 0.2896          | 0.2980 |
| 0.8849        | 40.98 | 15000 | 0.2727          | 0.2798 |
| 0.8665        | 49.18 | 18000 | 0.2662          | 0.2696 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
