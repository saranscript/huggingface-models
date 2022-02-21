---
language:
- sv-SE
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-common_voice-tr-demo
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-common_voice-tr-demo

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the COMMON_VOICE - SV-SE dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5528
- Wer: 0.3811

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
- num_epochs: 15.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 0.74  | 100  | 3.4444          | 1.0    |
| No log        | 1.47  | 200  | 2.9421          | 1.0    |
| No log        | 2.21  | 300  | 2.2802          | 1.0137 |
| No log        | 2.94  | 400  | 0.9683          | 0.7611 |
| 3.7264        | 3.68  | 500  | 0.7941          | 0.6594 |
| 3.7264        | 4.41  | 600  | 0.6695          | 0.5751 |
| 3.7264        | 5.15  | 700  | 0.6507          | 0.5314 |
| 3.7264        | 5.88  | 800  | 0.5731          | 0.4927 |
| 3.7264        | 6.62  | 900  | 0.5723          | 0.4580 |
| 0.4592        | 7.35  | 1000 | 0.5913          | 0.4479 |
| 0.4592        | 8.09  | 1100 | 0.5562          | 0.4423 |
| 0.4592        | 8.82  | 1200 | 0.5566          | 0.4292 |
| 0.4592        | 9.56  | 1300 | 0.5492          | 0.4303 |
| 0.4592        | 10.29 | 1400 | 0.5665          | 0.4331 |
| 0.2121        | 11.03 | 1500 | 0.5610          | 0.4084 |
| 0.2121        | 11.76 | 1600 | 0.5703          | 0.4014 |
| 0.2121        | 12.5  | 1700 | 0.5669          | 0.3898 |
| 0.2121        | 13.24 | 1800 | 0.5586          | 0.3962 |
| 0.2121        | 13.97 | 1900 | 0.5656          | 0.3897 |
| 0.1326        | 14.71 | 2000 | 0.5565          | 0.3813 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu113
- Datasets 1.18.0
- Tokenizers 0.10.3
