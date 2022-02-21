---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-ami_multi-nithin3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-ami_multi-nithin3

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9953
- Wer: 0.4577

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.7412        | 1.07  | 2500  | 2.9356          | 0.9925 |
| 2.0224        | 2.13  | 5000  | 2.0951          | 0.5730 |
| 1.9017        | 3.2   | 7500  | 1.8801          | 0.5070 |
| 1.8356        | 4.27  | 10000 | 2.0530          | 0.4778 |
| 1.8002        | 5.33  | 12500 | 1.9465          | 0.4620 |
| 1.7424        | 6.4   | 15000 | 1.9561          | 0.4529 |
| 1.7406        | 7.47  | 17500 | 1.9190          | 0.4477 |
| 1.7046        | 8.53  | 20000 | 1.8138          | 0.4402 |
| 1.6784        | 9.6   | 22500 | 1.8275          | 0.4385 |
| 1.6657        | 10.67 | 25000 | 1.7603          | 0.4307 |
| 1.6618        | 11.73 | 27500 | 1.7269          | 0.4249 |
| 1.6037        | 12.8  | 30000 | 1.7071          | 0.4272 |
| 1.639         | 13.87 | 32500 | 1.6559          | 0.4234 |
| 1.614         | 14.93 | 35000 | 1.7535          | 0.4237 |
| 1.6044        | 16.0  | 37500 | 1.7945          | 0.4200 |
| 1.5685        | 17.06 | 40000 | 1.7135          | 0.4170 |
| 1.6194        | 18.13 | 42500 | 1.8712          | 0.4161 |
| 1.566         | 19.2  | 45000 | 1.8720          | 0.4176 |
| 1.5572        | 20.26 | 47500 | 1.7077          | 0.4135 |
| 1.5715        | 21.33 | 50000 | 1.7538          | 0.4143 |
| 1.5595        | 22.4  | 52500 | 1.8135          | 0.4133 |
| 1.5465        | 23.46 | 55000 | 1.8119          | 0.4134 |
| 1.5369        | 24.53 | 57500 | 1.7565          | 0.4086 |
| 1.5392        | 25.6  | 60000 | 1.7323          | 0.4101 |
| 1.5383        | 26.66 | 62500 | 1.7516          | 0.4097 |
| 1.5266        | 27.73 | 65000 | 1.7961          | 0.4104 |
| 1.525         | 28.8  | 67500 | 1.7472          | 0.4094 |
| 1.5779        | 29.86 | 70000 | 1.7600          | 0.4096 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
