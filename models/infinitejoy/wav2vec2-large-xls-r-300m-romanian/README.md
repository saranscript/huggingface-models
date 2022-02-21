---
language:
- ro
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- ro
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Romanian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: ro
    metrics:
       - name: Test WER
         type: wer
         value: 14.194
       - name: Test CER
         type: cer
         value: 3.288
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: ro
    metrics:
       - name: Test WER
         type: wer
         value: 40.869
       - name: Test CER
         type: cer
         value: 12.049
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-romanian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - RO dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1167
- Wer: 0.1421

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
| 1.1973        | 8.89  | 2000  | 0.4481          | 0.4849 |
| 0.6005        | 17.78 | 4000  | 0.1420          | 0.1777 |
| 0.5248        | 26.67 | 6000  | 0.1303          | 0.1651 |
| 0.4871        | 35.56 | 8000  | 0.1207          | 0.1523 |
| 0.4428        | 44.44 | 10000 | 0.1143          | 0.1425 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
