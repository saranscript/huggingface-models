---
license: apache-2.0
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xlsr-53-W2V2-TR-MED
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-53-W2V2-TR-MED

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4467
- Wer: 0.4598

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
- num_epochs: 60
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.1343        | 4.21  | 400  | 2.3674          | 1.0372 |
| 0.8075        | 8.42  | 800  | 0.4583          | 0.6308 |
| 0.3209        | 12.63 | 1200 | 0.4291          | 0.5531 |
| 0.2273        | 16.84 | 1600 | 0.4348          | 0.5378 |
| 0.1764        | 21.05 | 2000 | 0.4550          | 0.5326 |
| 0.148         | 25.26 | 2400 | 0.4839          | 0.5319 |
| 0.1268        | 29.47 | 2800 | 0.4515          | 0.5070 |
| 0.1113        | 33.68 | 3200 | 0.4590          | 0.4930 |
| 0.1025        | 37.89 | 3600 | 0.4546          | 0.4888 |
| 0.0922        | 42.11 | 4000 | 0.4782          | 0.4852 |
| 0.082         | 46.32 | 4400 | 0.4605          | 0.4752 |
| 0.0751        | 50.53 | 4800 | 0.4358          | 0.4689 |
| 0.0699        | 54.74 | 5200 | 0.4359          | 0.4629 |
| 0.0633        | 58.95 | 5600 | 0.4467          | 0.4598 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
