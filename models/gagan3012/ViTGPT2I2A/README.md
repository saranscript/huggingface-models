---
license: apache-2.0
tags:
- image-captioning
- generated_from_trainer
model-index:
- name: ViTGPT2I2A
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# ViTGPT2I2A

This model is a fine-tuned version of [google/vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) on the vizwiz dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0708

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
- seed: 42
- distributed_type: multi-GPU
- num_devices: 2
- total_train_batch_size: 4
- total_eval_batch_size: 4
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 0.1528        | 0.17  | 1000  | 0.0869          |
| 0.0899        | 0.34  | 2000  | 0.0817          |
| 0.084         | 0.51  | 3000  | 0.0790          |
| 0.0814        | 0.68  | 4000  | 0.0773          |
| 0.0803        | 0.85  | 5000  | 0.0757          |
| 0.077         | 1.02  | 6000  | 0.0745          |
| 0.0739        | 1.19  | 7000  | 0.0740          |
| 0.0719        | 1.37  | 8000  | 0.0737          |
| 0.0717        | 1.54  | 9000  | 0.0730          |
| 0.0731        | 1.71  | 10000 | 0.0727          |
| 0.0708        | 1.88  | 11000 | 0.0720          |
| 0.0697        | 2.05  | 12000 | 0.0717          |
| 0.0655        | 2.22  | 13000 | 0.0719          |
| 0.0653        | 2.39  | 14000 | 0.0719          |
| 0.0657        | 2.56  | 15000 | 0.0712          |
| 0.0663        | 2.73  | 16000 | 0.0710          |
| 0.0654        | 2.9   | 17000 | 0.0708          |
| 0.0645        | 3.07  | 18000 | 0.0716          |
| 0.0616        | 3.24  | 19000 | 0.0712          |
| 0.0607        | 3.41  | 20000 | 0.0712          |
| 0.0611        | 3.58  | 21000 | 0.0711          |
| 0.0615        | 3.76  | 22000 | 0.0711          |
| 0.0614        | 3.93  | 23000 | 0.0710          |
| 0.0594        | 4.1   | 24000 | 0.0716          |
| 0.0587        | 4.27  | 25000 | 0.0715          |
| 0.0574        | 4.44  | 26000 | 0.0715          |
| 0.0579        | 4.61  | 27000 | 0.0715          |
| 0.0581        | 4.78  | 28000 | 0.0715          |
| 0.0579        | 4.95  | 29000 | 0.0715          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0
