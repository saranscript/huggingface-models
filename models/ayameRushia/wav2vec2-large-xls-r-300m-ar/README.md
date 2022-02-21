---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-ar
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-ar

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4819
- Wer: 0.4244

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
- eval_batch_size: 4
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 400
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 11.0435       | 0.67  | 400   | 4.3104          | 1.0    |
| 3.4451        | 1.34  | 800   | 3.1566          | 1.0    |
| 3.1399        | 2.01  | 1200  | 3.0532          | 0.9990 |
| 2.8538        | 2.68  | 1600  | 1.6994          | 0.9238 |
| 1.7195        | 3.35  | 2000  | 0.8867          | 0.6727 |
| 1.326         | 4.02  | 2400  | 0.6603          | 0.5834 |
| 1.1561        | 4.69  | 2800  | 0.5809          | 0.5479 |
| 1.0764        | 5.36  | 3200  | 0.5943          | 0.5495 |
| 1.0144        | 6.03  | 3600  | 0.5344          | 0.5251 |
| 0.965         | 6.7   | 4000  | 0.4844          | 0.4936 |
| 0.927         | 7.37  | 4400  | 0.5048          | 0.5019 |
| 0.8985        | 8.04  | 4800  | 0.5809          | 0.5267 |
| 0.8684        | 8.71  | 5200  | 0.4740          | 0.4753 |
| 0.8581        | 9.38  | 5600  | 0.4813          | 0.4834 |
| 0.8334        | 10.05 | 6000  | 0.4515          | 0.4545 |
| 0.8134        | 10.72 | 6400  | 0.4370          | 0.4543 |
| 0.8002        | 11.39 | 6800  | 0.4225          | 0.4384 |
| 0.7884        | 12.06 | 7200  | 0.4593          | 0.4565 |
| 0.7675        | 12.73 | 7600  | 0.4752          | 0.4680 |
| 0.7607        | 13.4  | 8000  | 0.4950          | 0.4771 |
| 0.7475        | 14.07 | 8400  | 0.4373          | 0.4391 |
| 0.7397        | 14.74 | 8800  | 0.4506          | 0.4541 |
| 0.7289        | 15.41 | 9200  | 0.4840          | 0.4691 |
| 0.722         | 16.08 | 9600  | 0.4701          | 0.4571 |
| 0.7067        | 16.75 | 10000 | 0.4561          | 0.4461 |
| 0.7033        | 17.42 | 10400 | 0.4384          | 0.4347 |
| 0.6915        | 18.09 | 10800 | 0.4424          | 0.4290 |
| 0.6854        | 18.76 | 11200 | 0.4635          | 0.4360 |
| 0.6813        | 19.43 | 11600 | 0.4280          | 0.4147 |
| 0.6776        | 20.1  | 12000 | 0.4610          | 0.4344 |
| 0.67          | 20.77 | 12400 | 0.4540          | 0.4367 |
| 0.6653        | 21.44 | 12800 | 0.4509          | 0.4234 |
| 0.6609        | 22.11 | 13200 | 0.4874          | 0.4444 |
| 0.6541        | 22.78 | 13600 | 0.4542          | 0.4230 |
| 0.6528        | 23.45 | 14000 | 0.4732          | 0.4373 |
| 0.6463        | 24.12 | 14400 | 0.4483          | 0.4188 |
| 0.6399        | 24.79 | 14800 | 0.4731          | 0.4341 |
| 0.6353        | 25.46 | 15200 | 0.5031          | 0.4412 |
| 0.6358        | 26.13 | 15600 | 0.4986          | 0.4397 |
| 0.6317        | 26.8  | 16000 | 0.5000          | 0.4360 |
| 0.6262        | 27.47 | 16400 | 0.4958          | 0.4318 |
| 0.6317        | 28.14 | 16800 | 0.4738          | 0.4234 |
| 0.6205        | 28.81 | 17200 | 0.4853          | 0.4262 |
| 0.6205        | 29.48 | 17600 | 0.4819          | 0.4244 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
