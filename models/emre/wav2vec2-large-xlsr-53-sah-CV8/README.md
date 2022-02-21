---
license: apache-2.0
language: sah
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xlsr-53-sah-CV8
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice sah
      type: common_voice
      args: sah
    metrics:
       - name: Test WER
         type: wer
         value: 56.06
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-53-sah-CV8

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5089
- Wer: 0.5606

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
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.6849        | 16.67 | 500  | 1.1135          | 0.9344 |
| 0.8223        | 33.33 | 1000 | 0.5148          | 0.5686 |
| 0.5477        | 50.0  | 1500 | 0.5089          | 0.5606 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.10.3
