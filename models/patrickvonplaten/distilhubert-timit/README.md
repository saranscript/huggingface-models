---
license: apache-2.0
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: distilhubert-timit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilhubert-timit

This model is a fine-tuned version of [ntu-spml/distilhubert](https://huggingface.co/ntu-spml/distilhubert) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3601
- Wer: 0.6776

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
- train_batch_size: 32
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 20.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.4447        | 0.69  | 100  | 4.9546          | 1.0    |
| 2.9499        | 1.38  | 200  | 2.9519          | 1.0    |
| 2.8989        | 2.07  | 300  | 2.8624          | 1.0    |
| 2.2076        | 2.76  | 400  | 2.1089          | 1.0008 |
| 1.4186        | 3.45  | 500  | 1.4112          | 0.9165 |
| 0.9951        | 4.14  | 600  | 1.1378          | 0.7701 |
| 0.9754        | 4.83  | 700  | 1.0152          | 0.7274 |
| 0.9364        | 5.52  | 800  | 0.9619          | 0.7011 |
| 0.6557        | 6.21  | 900  | 0.9144          | 0.6868 |
| 0.5681        | 6.9   | 1000 | 0.8899          | 0.6683 |
| 0.66          | 7.59  | 1100 | 0.8992          | 0.6654 |
| 0.6144        | 8.28  | 1200 | 0.9299          | 0.6898 |
| 0.4099        | 8.97  | 1300 | 0.9510          | 0.6674 |
| 0.3384        | 9.66  | 1400 | 0.9598          | 0.6612 |
| 0.3163        | 10.34 | 1500 | 0.9954          | 0.6612 |
| 0.4204        | 11.03 | 1600 | 1.0164          | 0.6607 |
| 0.1932        | 11.72 | 1700 | 1.0637          | 0.6658 |
| 0.1449        | 12.41 | 1800 | 1.1190          | 0.6652 |
| 0.1803        | 13.1  | 1900 | 1.1260          | 0.6689 |
| 0.328         | 13.79 | 2000 | 1.2186          | 0.6751 |
| 0.0838        | 14.48 | 2100 | 1.2591          | 0.6909 |
| 0.0766        | 15.17 | 2200 | 1.2529          | 0.6780 |
| 0.0956        | 15.86 | 2300 | 1.2537          | 0.6668 |
| 0.2339        | 16.55 | 2400 | 1.3210          | 0.6797 |
| 0.0431        | 17.24 | 2500 | 1.3241          | 0.6781 |
| 0.0508        | 17.93 | 2600 | 1.3184          | 0.6683 |
| 0.0616        | 18.62 | 2700 | 1.3728          | 0.6889 |
| 0.1608        | 19.31 | 2800 | 1.3572          | 0.6771 |
| 0.0378        | 20.0  | 2900 | 1.3601          | 0.6776 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
