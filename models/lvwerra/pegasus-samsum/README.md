---
tags:
- generated_from_trainer
datasets:
- samsum
model-index:
- name: pegasus-samsum
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-samsum

This model is a fine-tuned version of [google/pegasus-cnn_dailymail](https://huggingface.co/google/pegasus-cnn_dailymail) on the samsum dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4177

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
- train_batch_size: 1
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 0.4

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 1.6092        | 0.03  | 500  | 1.6488          |
| 1.9715        | 0.07  | 1000 | 1.5444          |
| 1.8325        | 0.1   | 1500 | 1.5093          |
| 1.876         | 0.14  | 2000 | 1.4890          |
| 1.3081        | 0.17  | 2500 | 1.4737          |
| 1.7769        | 0.2   | 3000 | 1.4496          |
| 1.6276        | 0.24  | 3500 | 1.4430          |
| 1.6624        | 0.27  | 4000 | 1.4288          |
| 1.9202        | 0.31  | 4500 | 1.4235          |
| 1.4404        | 0.34  | 5000 | 1.4189          |
| 1.8016        | 0.37  | 5500 | 1.4177          |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
