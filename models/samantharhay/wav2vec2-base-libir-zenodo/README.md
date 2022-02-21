---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
  name: wav2vec2-base-libir-zenodo
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-libir-zenodo

This model is a fine-tuned version of [facebook/wav2vec2-base-960h](https://huggingface.co/facebook/wav2vec2-base-960h) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4238
- Wer: 0.4336

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.053         | 1.0   | 31   | 3.1494          | 0.7345 |
| 2.9742        | 2.0   | 62   | 3.0527          | 0.7257 |
| 2.9139        | 3.0   | 93   | 2.8808          | 0.7257 |
| 2.6586        | 4.0   | 124  | 2.6648          | 0.6726 |
| 2.7117        | 5.0   | 155  | 2.4695          | 0.6372 |
| 2.5173        | 6.0   | 186  | 2.3087          | 0.6195 |
| 2.3665        | 7.0   | 217  | 2.2745          | 0.6018 |
| 2.1276        | 8.0   | 248  | 2.2180          | 0.5752 |
| 2.1624        | 9.0   | 279  | 2.1311          | 0.5752 |
| 2.0312        | 10.0  | 310  | 2.0358          | 0.5575 |
| 2.0652        | 11.0  | 341  | 1.9146          | 0.5310 |
| 1.7963        | 12.0  | 372  | 1.8346          | 0.5221 |
| 1.6811        | 13.0  | 403  | 1.8351          | 0.5398 |
| 1.5929        | 14.0  | 434  | 1.8256          | 0.4779 |
| 1.6644        | 15.0  | 465  | 1.7572          | 0.4779 |
| 1.5411        | 16.0  | 496  | 1.8740          | 0.4779 |
| 1.4027        | 17.0  | 527  | 1.5143          | 0.4779 |
| 1.2634        | 18.0  | 558  | 1.3864          | 0.4867 |
| 1.1053        | 19.0  | 589  | 1.3192          | 0.4425 |
| 1.0517        | 20.0  | 620  | 1.4705          | 0.4602 |
| 1.1033        | 21.0  | 651  | 1.6006          | 0.4956 |
| 0.9992        | 22.0  | 682  | 1.4748          | 0.5044 |
| 0.8987        | 23.0  | 713  | 1.3544          | 0.4867 |
| 0.9656        | 24.0  | 744  | 1.2673          | 0.4336 |
| 0.952         | 25.0  | 775  | 1.3955          | 0.4071 |
| 0.8507        | 26.0  | 806  | 1.3520          | 0.4425 |
| 0.8269        | 27.0  | 837  | 1.8992          | 0.4336 |
| 0.7255        | 28.0  | 868  | 1.9850          | 0.4425 |
| 0.8269        | 29.0  | 899  | 3.0089          | 0.4425 |
| 0.6178        | 30.0  | 930  | 1.4238          | 0.4336 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
