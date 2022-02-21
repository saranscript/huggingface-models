---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bert-large-uncased-finetuned-vi-infovqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-large-uncased-finetuned-vi-infovqa

This model is a fine-tuned version of [bert-large-uncased](https://huggingface.co/bert-large-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 7.4878

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 2
- eval_batch_size: 2
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 0.11  | 100  | 4.6256          |
| No log        | 0.21  | 200  | 4.4042          |
| No log        | 0.32  | 300  | 5.0021          |
| No log        | 0.43  | 400  | 4.2825          |
| 4.6758        | 0.53  | 500  | 4.3886          |
| 4.6758        | 0.64  | 600  | 4.2519          |
| 4.6758        | 0.75  | 700  | 4.2977          |
| 4.6758        | 0.85  | 800  | 3.9916          |
| 4.6758        | 0.96  | 900  | 4.1650          |
| 4.1715        | 1.07  | 1000 | 4.5001          |
| 4.1715        | 1.17  | 1100 | 4.0898          |
| 4.1715        | 1.28  | 1200 | 4.1623          |
| 4.1715        | 1.39  | 1300 | 4.3271          |
| 4.1715        | 1.49  | 1400 | 3.9661          |
| 3.7926        | 1.6   | 1500 | 3.8727          |
| 3.7926        | 1.71  | 1600 | 3.8934          |
| 3.7926        | 1.81  | 1700 | 3.7262          |
| 3.7926        | 1.92  | 1800 | 3.7701          |
| 3.7926        | 2.03  | 1900 | 3.7653          |
| 3.5041        | 2.13  | 2000 | 3.9261          |
| 3.5041        | 2.24  | 2100 | 4.0915          |
| 3.5041        | 2.35  | 2200 | 4.0348          |
| 3.5041        | 2.45  | 2300 | 4.0212          |
| 3.5041        | 2.56  | 2400 | 4.4653          |
| 2.8475        | 2.67  | 2500 | 4.2959          |
| 2.8475        | 2.77  | 2600 | 4.1039          |
| 2.8475        | 2.88  | 2700 | 3.8037          |
| 2.8475        | 2.99  | 2800 | 3.7552          |
| 2.8475        | 3.09  | 2900 | 4.2476          |
| 2.5488        | 3.2   | 3000 | 4.6716          |
| 2.5488        | 3.3   | 3100 | 4.7058          |
| 2.5488        | 3.41  | 3200 | 4.6266          |
| 2.5488        | 3.52  | 3300 | 4.5697          |
| 2.5488        | 3.62  | 3400 | 5.1017          |
| 2.0347        | 3.73  | 3500 | 4.6254          |
| 2.0347        | 3.84  | 3600 | 4.4822          |
| 2.0347        | 3.94  | 3700 | 4.9413          |
| 2.0347        | 4.05  | 3800 | 5.3600          |
| 2.0347        | 4.16  | 3900 | 5.7323          |
| 1.6566        | 4.26  | 4000 | 5.8822          |
| 1.6566        | 4.37  | 4100 | 6.0173          |
| 1.6566        | 4.48  | 4200 | 5.6688          |
| 1.6566        | 4.58  | 4300 | 6.0617          |
| 1.6566        | 4.69  | 4400 | 6.6631          |
| 1.3348        | 4.8   | 4500 | 6.0290          |
| 1.3348        | 4.9   | 4600 | 6.2455          |
| 1.3348        | 5.01  | 4700 | 6.0963          |
| 1.3348        | 5.12  | 4800 | 7.0983          |
| 1.3348        | 5.22  | 4900 | 7.5483          |
| 1.0701        | 5.33  | 5000 | 7.7187          |
| 1.0701        | 5.44  | 5100 | 7.4630          |
| 1.0701        | 5.54  | 5200 | 7.1394          |
| 1.0701        | 5.65  | 5300 | 7.0703          |
| 1.0701        | 5.76  | 5400 | 7.5611          |
| 0.9414        | 5.86  | 5500 | 7.6038          |
| 0.9414        | 5.97  | 5600 | 7.4878          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
