---

model-index:
- name: qa-indo-k
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# qa-indo-k

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.4984

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.2537        | 1.0   | 8209  | 1.9642          |
| 0.943         | 2.0   | 16418 | 2.2143          |
| 0.6694        | 3.0   | 24627 | 2.4984          |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.0
- Datasets 1.11.0
- Tokenizers 0.10.3
