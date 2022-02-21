---
license: apache-2.0
language: tr
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-Tr-med-CommonVoice8
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice tr
      type: common_voice
      args: tr
    metrics:
       - name: Test WER
         type: wer
         value: 49.14

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-Tr-med-CommonVoice8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2556
- Wer: 0.4914

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 300
- num_epochs: 20
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.4876        | 6.66  | 5000  | 0.3252          | 0.5784 |
| 0.6919        | 13.32 | 10000 | 0.2720          | 0.5172 |
| 0.5919        | 19.97 | 15000 | 0.2556          | 0.4914 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.10.3
