---
license: apache-2.0
tags:
- generated_from_trainer

pipeline_tag: automatic-speech-recognition

model-index:
  name: iloko_model
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# iloko_model

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0095
- Wer: 0.0840

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.2784        | 1.11  | 100  | 2.9875          | 1.0    |
| 2.6899        | 2.22  | 200  | 2.6741          | 1.0    |
| 2.6177        | 3.33  | 300  | 2.6516          | 1.0    |
| 2.5327        | 4.44  | 400  | 2.4530          | 1.0    |
| 0.8653        | 5.56  | 500  | 0.5227          | 0.6547 |
| 0.3414        | 6.67  | 600  | 0.1830          | 0.2487 |
| 0.2299        | 7.78  | 700  | 0.1212          | 0.1877 |
| 0.1739        | 8.89  | 800  | 0.0843          | 0.1441 |
| 0.1242        | 10.0  | 900  | 0.0766          | 0.1441 |
| 0.1116        | 11.11 | 1000 | 0.0530          | 0.1145 |
| 0.0861        | 12.22 | 1100 | 0.0442          | 0.1047 |
| 0.1007        | 13.33 | 1200 | 0.0379          | 0.1023 |
| 0.0613        | 14.44 | 1300 | 0.0291          | 0.1006 |
| 0.0629        | 15.56 | 1400 | 0.0264          | 0.0961 |
| 0.047         | 16.67 | 1500 | 0.0238          | 0.0935 |
| 0.0797        | 17.78 | 1600 | 0.0226          | 0.0913 |
| 0.034         | 18.89 | 1700 | 0.0197          | 0.0893 |
| 0.0485        | 20.0  | 1800 | 0.0173          | 0.0905 |
| 0.0402        | 21.11 | 1900 | 0.0148          | 0.0902 |
| 0.0231        | 22.22 | 2000 | 0.0135          | 0.0891 |
| 0.0512        | 23.33 | 2100 | 0.0134          | 0.0861 |
| 0.0181        | 24.44 | 2200 | 0.0118          | 0.0842 |
| 0.0371        | 25.56 | 2300 | 0.0116          | 0.0867 |
| 0.0342        | 26.67 | 2400 | 0.0104          | 0.0863 |
| 0.0344        | 27.78 | 2500 | 0.0100          | 0.0850 |
| 0.0182        | 28.89 | 2600 | 0.0096          | 0.0839 |
| 0.0171        | 30.0  | 2700 | 0.0095          | 0.0840 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu102
- Datasets 1.13.3
- Tokenizers 0.10.3
