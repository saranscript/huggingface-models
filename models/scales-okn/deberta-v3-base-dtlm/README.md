---
license: mit
tags:
- generated_from_trainer
model-index:
- name: dev-lm-fast
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# dev-lm-fast

This model is a fine-tuned version of [microsoft/deberta-v3-base](https://huggingface.co/microsoft/deberta-v3-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8148

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1.0

### Training results

| Training Loss | Epoch | Step   | Validation Loss |
|:-------------:|:-----:|:------:|:---------------:|
| 1.7242        | 0.02  | 15000  | 1.6151          |
| 1.4916        | 0.04  | 30000  | 1.4046          |
| 1.3764        | 0.06  | 45000  | 1.2586          |
| 1.2939        | 0.08  | 60000  | 1.2500          |
| 1.2529        | 0.1   | 75000  | 1.1612          |
| 1.1913        | 0.12  | 90000  | 1.1410          |
| 1.1712        | 0.15  | 105000 | 1.0923          |
| 1.1435        | 0.17  | 120000 | 1.0421          |
| 1.1156        | 0.19  | 135000 | 1.0778          |
| 1.1105        | 0.21  | 150000 | 1.0409          |
| 1.0968        | 0.23  | 165000 | 1.0334          |
| 1.0829        | 0.25  | 180000 | 1.0151          |
| 1.0591        | 0.27  | 195000 | 0.9855          |
| 1.0606        | 0.29  | 210000 | 0.9567          |
| 1.0556        | 0.31  | 225000 | 0.9461          |
| 1.0349        | 0.33  | 240000 | 0.9628          |
| 1.0323        | 0.35  | 255000 | 0.9434          |
| 1.0055        | 0.37  | 270000 | 0.9502          |
| 1.0044        | 0.39  | 285000 | 0.9646          |
| 0.9886        | 0.42  | 300000 | 0.9216          |
| 0.9783        | 0.44  | 315000 | 0.9166          |
| 0.9646        | 0.46  | 330000 | 0.9277          |
| 0.9767        | 0.48  | 345000 | 0.8874          |
| 0.9653        | 0.5   | 360000 | 0.9212          |
| 0.95          | 0.52  | 375000 | 0.8993          |
| 0.947         | 0.54  | 390000 | 0.8900          |
| 0.9501        | 0.56  | 405000 | 0.8936          |
| 0.9505        | 0.58  | 420000 | 0.8920          |
| 0.9534        | 0.6   | 435000 | 0.8688          |
| 0.9412        | 0.62  | 450000 | 0.8820          |
| 0.9269        | 0.64  | 465000 | 0.8507          |
| 0.9237        | 0.66  | 480000 | 0.8848          |
| 0.9153        | 0.69  | 495000 | 0.8481          |
| 0.9132        | 0.71  | 510000 | 0.8403          |
| 0.8967        | 0.73  | 525000 | 0.8634          |
| 0.901         | 0.75  | 540000 | 0.8334          |
| 0.8941        | 0.77  | 555000 | 0.8441          |
| 0.9084        | 0.79  | 570000 | 0.8088          |
| 0.9238        | 0.81  | 585000 | 0.8470          |
| 0.8642        | 0.83  | 600000 | 0.8108          |
| 0.8887        | 0.85  | 615000 | 0.8180          |
| 0.8819        | 0.87  | 630000 | 0.8174          |
| 0.8807        | 0.89  | 645000 | 0.8235          |
| 0.896         | 0.91  | 660000 | 0.8298          |
| 0.8735        | 0.93  | 675000 | 0.8041          |
| 0.8616        | 0.96  | 690000 | 0.8353          |
| 0.8727        | 0.98  | 705000 | 0.7769          |
| 0.8737        | 1.0   | 720000 | 0.7964          |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu113
- Datasets 1.15.1
- Tokenizers 0.10.3
