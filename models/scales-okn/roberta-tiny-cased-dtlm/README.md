---
tags:
- generated_from_trainer
model-index:
- name: roberta-tiny-cased-dtlm
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-tiny-cased-dtlm

This model is a fine-tuned version of [haisongzhang/roberta-tiny-cased](https://huggingface.co/haisongzhang/roberta-tiny-cased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7666

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 256
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1.0

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.8352        | 0.02  | 1000  | 1.5408          |
| 1.5206        | 0.04  | 2000  | 1.3241          |
| 1.3632        | 0.07  | 3000  | 1.2009          |
| 1.2699        | 0.09  | 4000  | 1.1458          |
| 1.1912        | 0.11  | 5000  | 1.0766          |
| 1.139         | 0.13  | 6000  | 1.0399          |
| 1.0983        | 0.16  | 7000  | 0.9807          |
| 1.0713        | 0.18  | 8000  | 0.9636          |
| 1.0458        | 0.2   | 9000  | 0.9266          |
| 1.0226        | 0.22  | 10000 | 0.9323          |
| 1.0037        | 0.24  | 11000 | 0.9036          |
| 0.9845        | 0.27  | 12000 | 0.9034          |
| 0.9746        | 0.29  | 13000 | 0.8766          |
| 0.964         | 0.31  | 14000 | 0.8716          |
| 0.9495        | 0.33  | 15000 | 0.8442          |
| 0.9396        | 0.35  | 16000 | 0.8558          |
| 0.9287        | 0.38  | 17000 | 0.8312          |
| 0.9161        | 0.4   | 18000 | 0.8311          |
| 0.9123        | 0.42  | 19000 | 0.8413          |
| 0.9054        | 0.44  | 20000 | 0.8079          |
| 0.893         | 0.47  | 21000 | 0.8140          |
| 0.8921        | 0.49  | 22000 | 0.8022          |
| 0.8856        | 0.51  | 23000 | 0.8084          |
| 0.8792        | 0.53  | 24000 | 0.8184          |
| 0.8731        | 0.55  | 25000 | 0.8000          |
| 0.8684        | 0.58  | 26000 | 0.7703          |
| 0.8616        | 0.6   | 27000 | 0.7917          |
| 0.8637        | 0.62  | 28000 | 0.7894          |
| 0.8592        | 0.64  | 29000 | 0.7800          |
| 0.8517        | 0.66  | 30000 | 0.7636          |
| 0.8501        | 0.69  | 31000 | 0.7405          |
| 0.8503        | 0.71  | 32000 | 0.7620          |
| 0.8422        | 0.73  | 33000 | 0.7395          |
| 0.8364        | 0.75  | 34000 | 0.7688          |
| 0.8394        | 0.78  | 35000 | 0.7653          |
| 0.8392        | 0.8   | 36000 | 0.7412          |
| 0.834         | 0.82  | 37000 | 0.7300          |
| 0.8377        | 0.84  | 38000 | 0.7695          |
| 0.8313        | 0.86  | 39000 | 0.7598          |
| 0.8266        | 0.89  | 40000 | 0.7659          |
| 0.8288        | 0.91  | 41000 | 0.7277          |
| 0.8271        | 0.93  | 42000 | 0.7491          |
| 0.8251        | 0.95  | 43000 | 0.7375          |
| 0.8246        | 0.97  | 44000 | 0.7190          |
| 0.8271        | 1.0   | 45000 | 0.7318          |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu113
- Datasets 1.15.1
- Tokenizers 0.10.3
