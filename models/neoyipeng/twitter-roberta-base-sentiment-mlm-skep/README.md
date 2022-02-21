---

model-index:
- name: twitter-roberta-base-sentiment-mlm-skep
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# twitter-roberta-base-sentiment-mlm-skep

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0003

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- num_epochs: 20
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 0.0122        | 1.0   | 936  | 0.0026          |
| 0.0003        | 2.0   | 1872 | 0.0003          |
| 0.0002        | 3.0   | 2808 | 0.0003          |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.0
- Datasets 1.11.0
- Tokenizers 0.10.3
