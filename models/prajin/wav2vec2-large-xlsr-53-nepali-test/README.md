---
language:
- ne
license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- openslr
model-index:
- name: wav2vec2-large-xlsr-53-nepali-test
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: openslr 
      type: openslr
      args: ne
    metrics:
       - name: Test WER
         type: wer
         value: 67.83
       
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-53-nepali-test

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4601
- Wer: 0.6783

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
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 7.7821        | 1.28  | 400   | 3.2052          | 1.0003 |
| 1.9443        | 2.56  | 800   | 0.7338          | 1.0301 |
| 0.7656        | 3.84  | 1200  | 0.5165          | 0.9149 |
| 0.5543        | 5.13  | 1600  | 0.4498          | 0.8551 |
| 0.4398        | 6.41  | 2000  | 0.4472          | 0.8139 |
| 0.3911        | 7.69  | 2400  | 0.4071          | 0.7938 |
| 0.3374        | 8.97  | 2800  | 0.4210          | 0.7897 |
| 0.2847        | 10.26 | 3200  | 0.4379          | 0.7693 |
| 0.2586        | 11.54 | 3600  | 0.3983          | 0.7523 |
| 0.239         | 12.82 | 4000  | 0.4140          | 0.7537 |
| 0.2141        | 14.1  | 4400  | 0.4165          | 0.7319 |
| 0.1979        | 15.38 | 4800  | 0.4247          | 0.7402 |
| 0.1901        | 16.67 | 5200  | 0.4212          | 0.7388 |
| 0.1802        | 17.95 | 5600  | 0.4359          | 0.7247 |
| 0.1619        | 19.23 | 6000  | 0.4499          | 0.7292 |
| 0.1622        | 20.51 | 6400  | 0.4226          | 0.7260 |
| 0.1591        | 21.79 | 6800  | 0.4339          | 0.7319 |
| 0.1391        | 23.08 | 7200  | 0.4344          | 0.7167 |
| 0.1373        | 24.36 | 7600  | 0.4451          | 0.7215 |
| 0.1293        | 25.64 | 8000  | 0.4216          | 0.7195 |
| 0.1197        | 26.92 | 8400  | 0.4471          | 0.7143 |
| 0.12          | 28.2  | 8800  | 0.4718          | 0.7119 |
| 0.1128        | 29.49 | 9200  | 0.4883          | 0.7032 |
| 0.1084        | 30.77 | 9600  | 0.5145          | 0.7129 |
| 0.1018        | 32.05 | 10000 | 0.4833          | 0.7115 |
| 0.0984        | 33.33 | 10400 | 0.5101          | 0.7029 |
| 0.0903        | 34.61 | 10800 | 0.4645          | 0.6942 |
| 0.0835        | 35.9  | 11200 | 0.4666          | 0.6966 |
| 0.0828        | 37.18 | 11600 | 0.4648          | 0.6939 |
| 0.0751        | 38.46 | 12000 | 0.4773          | 0.6870 |
| 0.0711        | 39.74 | 12400 | 0.4611          | 0.6949 |
| 0.068         | 41.03 | 12800 | 0.4525          | 0.6963 |
| 0.0615        | 42.31 | 13200 | 0.4702          | 0.6883 |
| 0.0574        | 43.59 | 13600 | 0.4822          | 0.6883 |
| 0.0573        | 44.87 | 14000 | 0.4722          | 0.6894 |
| 0.0563        | 46.15 | 14400 | 0.4578          | 0.6811 |
| 0.0497        | 47.44 | 14800 | 0.4637          | 0.6797 |
| 0.0487        | 48.72 | 15200 | 0.4656          | 0.6793 |
| 0.0468        | 50.0  | 15600 | 0.4601          | 0.6783 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
