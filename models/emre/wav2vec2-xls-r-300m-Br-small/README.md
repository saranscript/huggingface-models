---
license: apache-2.0
language: br
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-Br-small
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice br
      type: common_voice
      args: br
    metrics:
       - name: Test WER
         type: wer
         value: 66.75
---


# wav2vec2-xls-r-300m-Br-small

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0573
- Wer: 0.6675

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.7464        | 2.79  | 400  | 1.7474          | 1.1018 |
| 1.1117        | 5.59  | 800  | 0.9434          | 0.8697 |
| 0.6481        | 8.39  | 1200 | 0.9251          | 0.7910 |
| 0.4754        | 11.19 | 1600 | 0.9208          | 0.7412 |
| 0.3602        | 13.98 | 2000 | 0.9284          | 0.7232 |
| 0.2873        | 16.78 | 2400 | 0.9299          | 0.6940 |
| 0.2386        | 19.58 | 2800 | 1.0182          | 0.6927 |
| 0.1971        | 22.38 | 3200 | 1.0456          | 0.6898 |
| 0.1749        | 25.17 | 3600 | 1.0208          | 0.6769 |
| 0.1487        | 27.97 | 4000 | 1.0573          | 0.6675 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
