---
license: apache-2.0
language:
- lv
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-1B-common_voice7-lv-ft
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: lv
    metrics:
       - name: Test WER
         type: wer
         value: 11.179
       - name: Test CER
         type: cer
         value: 02.78         
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-1B-common_voice7-lv-ft

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1582
- Wer: 0.1137

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 24
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 48
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 900
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.6292        | 5.26  | 500  | 1.5562          | 0.9263 |
| 0.1303        | 10.53 | 1000 | 0.8107          | 0.7666 |
| 0.0974        | 15.79 | 1500 | 0.5290          | 0.4979 |
| 0.0724        | 21.05 | 2000 | 0.2941          | 0.2247 |
| 0.0591        | 26.32 | 2500 | 0.2838          | 0.2125 |
| 0.0494        | 31.58 | 3000 | 0.2589          | 0.2102 |
| 0.0417        | 36.84 | 3500 | 0.1987          | 0.1760 |
| 0.0375        | 42.11 | 4000 | 0.1934          | 0.1690 |
| 0.031         | 47.37 | 4500 | 0.1630          | 0.1460 |
| 0.027         | 52.63 | 5000 | 0.1957          | 0.1447 |
| 0.0256        | 57.89 | 5500 | 0.1747          | 0.1368 |
| 0.0206        | 63.16 | 6000 | 0.1602          | 0.1299 |
| 0.0178        | 68.42 | 6500 | 0.1809          | 0.1273 |
| 0.0154        | 73.68 | 7000 | 0.1686          | 0.1216 |
| 0.0137        | 78.95 | 7500 | 0.1585          | 0.1241 |
| 0.0128        | 84.21 | 8000 | 0.1783          | 0.1278 |
| 0.011         | 89.47 | 8500 | 0.1653          | 0.1228 |
| 0.0096        | 94.74 | 9000 | 0.1620          | 0.1161 |
| 0.0091        | 100.0 | 9500 | 0.1582          | 0.1137 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3
