---
tags:
- generated_from_trainer
- image-to-text
model-index:
- name: ViTGPT2_vizwiz
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# ViTGPT2_vizwiz

This model is a fine-tuned version of [](https://huggingface.co/) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0719

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 0.1207        | 0.07  | 1000  | 0.0906          |
| 0.0916        | 0.14  | 2000  | 0.0861          |
| 0.0879        | 0.2   | 3000  | 0.0840          |
| 0.0856        | 0.27  | 4000  | 0.0822          |
| 0.0834        | 0.34  | 5000  | 0.0806          |
| 0.0817        | 0.41  | 6000  | 0.0795          |
| 0.0812        | 0.48  | 7000  | 0.0785          |
| 0.0808        | 0.55  | 8000  | 0.0779          |
| 0.0796        | 0.61  | 9000  | 0.0771          |
| 0.0786        | 0.68  | 10000 | 0.0767          |
| 0.0774        | 0.75  | 11000 | 0.0762          |
| 0.0772        | 0.82  | 12000 | 0.0758          |
| 0.0756        | 0.89  | 13000 | 0.0754          |
| 0.0759        | 0.96  | 14000 | 0.0750          |
| 0.0756        | 1.02  | 15000 | 0.0748          |
| 0.0726        | 1.09  | 16000 | 0.0745          |
| 0.0727        | 1.16  | 17000 | 0.0745          |
| 0.0715        | 1.23  | 18000 | 0.0742          |
| 0.0726        | 1.3   | 19000 | 0.0741          |
| 0.072         | 1.37  | 20000 | 0.0738          |
| 0.0723        | 1.43  | 21000 | 0.0735          |
| 0.0715        | 1.5   | 22000 | 0.0734          |
| 0.0724        | 1.57  | 23000 | 0.0732          |
| 0.0723        | 1.64  | 24000 | 0.0730          |
| 0.0718        | 1.71  | 25000 | 0.0729          |
| 0.07          | 1.78  | 26000 | 0.0728          |
| 0.0702        | 1.84  | 27000 | 0.0726          |
| 0.0704        | 1.91  | 28000 | 0.0725          |
| 0.0703        | 1.98  | 29000 | 0.0725          |
| 0.0686        | 2.05  | 30000 | 0.0726          |
| 0.0687        | 2.12  | 31000 | 0.0726          |
| 0.0688        | 2.19  | 32000 | 0.0724          |
| 0.0677        | 2.25  | 33000 | 0.0724          |
| 0.0665        | 2.32  | 34000 | 0.0725          |
| 0.0684        | 2.39  | 35000 | 0.0723          |
| 0.0678        | 2.46  | 36000 | 0.0722          |
| 0.0686        | 2.53  | 37000 | 0.0722          |
| 0.067         | 2.59  | 38000 | 0.0721          |
| 0.0669        | 2.66  | 39000 | 0.0721          |
| 0.0673        | 2.73  | 40000 | 0.0721          |
| 0.0673        | 2.8   | 41000 | 0.0720          |
| 0.0662        | 2.87  | 42000 | 0.0720          |
| 0.0681        | 2.94  | 43000 | 0.0719          |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
