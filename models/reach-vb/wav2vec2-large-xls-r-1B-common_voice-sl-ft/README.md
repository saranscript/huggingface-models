---
license: apache-2.0
language:
- sl
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-1B-common_voice-sl-ft
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
         value: 23.26
       - name: Test CER
         type: cer
         value: 07.95  
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-1B-common_voice-sl-ft

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2112
- Wer: 0.1404

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
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 400
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.8291        | 12.2  | 500  | 0.5674          | 0.7611 |
| 0.0416        | 24.39 | 1000 | 0.3093          | 0.2964 |
| 0.0256        | 36.59 | 1500 | 0.2224          | 0.2072 |
| 0.0179        | 48.78 | 2000 | 0.2274          | 0.1960 |
| 0.0113        | 60.98 | 2500 | 0.2078          | 0.1582 |
| 0.0086        | 73.17 | 3000 | 0.1898          | 0.1552 |
| 0.0059        | 85.37 | 3500 | 0.2054          | 0.1446 |
| 0.0044        | 97.56 | 4000 | 0.2112          | 0.1404 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3
