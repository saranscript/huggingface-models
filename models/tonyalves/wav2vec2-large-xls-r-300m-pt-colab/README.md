---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-pt-colab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-pt-colab

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3637
- Wer: 0.2982

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
| 4.591         | 1.15  | 400   | 0.9128          | 0.6517 |
| 0.5049        | 2.31  | 800   | 0.4596          | 0.4437 |
| 0.2871        | 3.46  | 1200  | 0.3964          | 0.3905 |
| 0.2077        | 4.61  | 1600  | 0.3958          | 0.3744 |
| 0.1695        | 5.76  | 2000  | 0.4040          | 0.3720 |
| 0.1478        | 6.92  | 2400  | 0.3866          | 0.3651 |
| 0.1282        | 8.07  | 2800  | 0.3987          | 0.3674 |
| 0.1134        | 9.22  | 3200  | 0.4128          | 0.3688 |
| 0.1048        | 10.37 | 3600  | 0.3928          | 0.3561 |
| 0.0938        | 11.53 | 4000  | 0.4048          | 0.3619 |
| 0.0848        | 12.68 | 4400  | 0.4229          | 0.3555 |
| 0.0798        | 13.83 | 4800  | 0.3974          | 0.3468 |
| 0.0688        | 14.98 | 5200  | 0.3870          | 0.3503 |
| 0.0658        | 16.14 | 5600  | 0.3875          | 0.3351 |
| 0.061         | 17.29 | 6000  | 0.4133          | 0.3417 |
| 0.0569        | 18.44 | 6400  | 0.3915          | 0.3414 |
| 0.0526        | 19.6  | 6800  | 0.3957          | 0.3231 |
| 0.0468        | 20.75 | 7200  | 0.4110          | 0.3301 |
| 0.0407        | 21.9  | 7600  | 0.3866          | 0.3186 |
| 0.0384        | 23.05 | 8000  | 0.3976          | 0.3193 |
| 0.0363        | 24.21 | 8400  | 0.3910          | 0.3177 |
| 0.0313        | 25.36 | 8800  | 0.3656          | 0.3109 |
| 0.0293        | 26.51 | 9200  | 0.3712          | 0.3092 |
| 0.0277        | 27.66 | 9600  | 0.3613          | 0.3054 |
| 0.0249        | 28.82 | 10000 | 0.3783          | 0.3015 |
| 0.0234        | 29.97 | 10400 | 0.3637          | 0.2982 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu102
- Datasets 1.13.3
- Tokenizers 0.10.3
