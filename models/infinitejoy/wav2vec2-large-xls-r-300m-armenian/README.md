---
language:
- hy-AM
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Armenian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: hy-AM
    metrics:
       - name: Test WER
         type: wer
         value: 101.627
       - name: Test CER
         type: cer
         value: 158.767
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-armenian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - HY-AM dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9669
- Wer: 0.6942

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
- num_epochs: 200.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 1.7294        | 27.78  | 500  | 0.8540          | 0.9944 |
| 0.8863        | 55.56  | 1000 | 0.7282          | 0.7312 |
| 0.5789        | 83.33  | 1500 | 0.8178          | 0.8102 |
| 0.3899        | 111.11 | 2000 | 0.8034          | 0.7701 |
| 0.2869        | 138.89 | 2500 | 0.9061          | 0.6999 |
| 0.1934        | 166.67 | 3000 | 0.9400          | 0.7105 |
| 0.1551        | 194.44 | 3500 | 0.9667          | 0.6955 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
