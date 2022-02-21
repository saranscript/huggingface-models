---

model-index:
- name: twitter-roberta-base-sentiment-mlm
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# twitter-roberta-base-sentiment-mlm

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.5119

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
| 6.9349        | 1.0   | 610  | 4.9601          |
| 4.7855        | 2.0   | 1220 | 4.0446          |
| 4.0519        | 3.0   | 1830 | 3.5383          |
| 3.6449        | 4.0   | 2440 | 3.2304          |
| 3.3727        | 5.0   | 3050 | 3.0593          |
| 3.1631        | 6.0   | 3660 | 2.8956          |
| 3.024         | 7.0   | 4270 | 2.8550          |
| 2.9008        | 8.0   | 4880 | 2.7255          |
| 2.8076        | 9.0   | 5490 | 2.6705          |
| 2.7414        | 10.0  | 6100 | 2.6554          |
| 2.6757        | 11.0  | 6710 | 2.5601          |
| 2.6246        | 12.0  | 7320 | 2.4616          |
| 2.5754        | 13.0  | 7930 | 2.5119          |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.0
- Datasets 1.11.0
- Tokenizers 0.10.3
