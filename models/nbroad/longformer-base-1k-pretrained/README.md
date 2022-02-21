---
tags:
- generated_from_trainer
model-index:
- name: longformer-base-1k-pretrained
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# longformer-base-1k-pretrained

This is [allenai/longformer-base-4096](https://huggingface.co/allenai/longformer-base-4096) trained using Masked Language Modeling on the student essays in the Feedback Prize - Evaluating Student Writing Kaggle Competition. Data is available here: https://www.kaggle.com/c/feedback-prize-2021/data
It achieves the following results on the evaluation set:
- Loss: 1.1687

## Model description

This is allenai/longformer-base-4096 trained at 1024 sequence length.

## Intended uses & limitations

In-domain pretraining should help finetuning for the competition.

## Training and evaluation data

A collection of student essays. No modifications made to the files available here: https://www.kaggle.com/c/feedback-prize-2021/data

I split off 5% of the files to be used as the validation set.

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 8e-05
- train_batch_size: 8
- eval_batch_size: 16
- seed: 2021
- distributed_type: multi-GPU
- num_devices: 3
- total_train_batch_size: 24
- total_eval_batch_size: 48
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 5.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 1.4877        | 0.49  | 150  | 1.3727          |
| 1.4191        | 0.97  | 300  | 1.2795          |
| 1.3569        | 1.46  | 450  | 1.2764          |
| 1.3429        | 1.94  | 600  | 1.2666          |
| 1.3013        | 2.43  | 750  | 1.2276          |
| 1.2754        | 2.91  | 900  | 1.2054          |
| 1.2637        | 3.4   | 1050 | 1.2231          |
| 1.2379        | 3.88  | 1200 | 1.1901          |
| 1.23          | 4.37  | 1350 | 1.2083          |
| 1.2184        | 4.85  | 1500 | 1.1887          |


### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.9.0a0+c3d40fd
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
