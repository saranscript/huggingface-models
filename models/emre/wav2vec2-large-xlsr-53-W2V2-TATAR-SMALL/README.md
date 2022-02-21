---
license: apache-2.0
language: tt
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- tt
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xlsr-53-W2V2-TATAR-SMALL
  results: 
  - task:
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: tt
    metrics:
      - name: Test WER
        type: wer
        value: 53.16
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-53-W2V2-TATAR-SMALL

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4714
- Wer: 0.5316

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

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 6.2446        | 1.17  | 400   | 3.2621          | 1.0    |
| 1.739         | 2.35  | 800   | 0.5832          | 0.7688 |
| 0.4718        | 3.52  | 1200  | 0.4785          | 0.6824 |
| 0.3574        | 4.69  | 1600  | 0.4814          | 0.6792 |
| 0.2946        | 5.86  | 2000  | 0.4484          | 0.6506 |
| 0.2674        | 7.04  | 2400  | 0.4612          | 0.6225 |
| 0.2349        | 8.21  | 2800  | 0.4600          | 0.6050 |
| 0.2206        | 9.38  | 3200  | 0.4772          | 0.6048 |
| 0.2072        | 10.56 | 3600  | 0.4676          | 0.6106 |
| 0.1984        | 11.73 | 4000  | 0.4816          | 0.6079 |
| 0.1793        | 12.9  | 4400  | 0.4616          | 0.5836 |
| 0.172         | 14.08 | 4800  | 0.4808          | 0.5860 |
| 0.1624        | 15.25 | 5200  | 0.4854          | 0.5820 |
| 0.156         | 16.42 | 5600  | 0.4609          | 0.5656 |
| 0.1448        | 17.59 | 6000  | 0.4926          | 0.5817 |
| 0.1406        | 18.77 | 6400  | 0.4638          | 0.5654 |
| 0.1337        | 19.94 | 6800  | 0.4731          | 0.5652 |
| 0.1317        | 21.11 | 7200  | 0.4861          | 0.5639 |
| 0.1179        | 22.29 | 7600  | 0.4766          | 0.5521 |
| 0.1197        | 23.46 | 8000  | 0.4824          | 0.5584 |
| 0.1096        | 24.63 | 8400  | 0.5006          | 0.5559 |
| 0.1038        | 25.81 | 8800  | 0.4994          | 0.5440 |
| 0.0992        | 26.98 | 9200  | 0.4867          | 0.5405 |
| 0.0984        | 28.15 | 9600  | 0.4798          | 0.5361 |
| 0.0943        | 29.33 | 10000 | 0.4714          | 0.5316 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
