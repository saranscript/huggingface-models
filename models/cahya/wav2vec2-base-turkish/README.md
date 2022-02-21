---
language:
- tr
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- tr
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: Wav2Vec2 Base Turkish by Cahya
  results:
  - task:
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: tr
    metrics:
      - name: Test WER
        type: wer
        value: 8.147
      - name: Test CER
        type: cer
        value: 2.802
  - task:
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: tr
    metrics:
      - name: Test WER
        type: wer
        value: 28.011
      - name: Test CER
        type: cer
        value: 10.66
---
      
# 

This model is a fine-tuned version of [cahya/wav2vec2-base-turkish-artificial-cv](https://huggingface.co/cahya/wav2vec2-base-turkish-artificial-cv) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1337
- Wer: 0.1353

 
|     | Dataset                       | WER     | CER      |
|---|-------------------------------|---------|----------|
| 1   | Common Voice 6.1              |  9.437  |  3.325   |
| 2   | Common Voice 7.0              |  8.147  |  2.802   |
| 3   | Common Voice 8.0              |  8.335  |  2.336   |
| 4   | Speech Recognition Community  | 28.011  | 10.66    |

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data
The following datasets were used for finetuning:
 - [Common Voice 7.0 TR](https://huggingface.co/datasets/mozilla-foundation/common_voice_7_0) 'train', 'validation' and 'other' split were used for training.
 - [Media Speech](https://www.openslr.org/108/)
 - [Magic Hub](https://magichub.com/)


## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-06
- train_batch_size: 6
- eval_batch_size: 2
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 24
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 5.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.1224        | 3.45  | 500  | 0.1641          | 0.1396 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.2
- Tokenizers 0.10.3
