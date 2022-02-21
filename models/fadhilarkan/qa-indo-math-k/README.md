---

model-index:
- name: qa-indo-math-k
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# qa-indo-math-k

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8801

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
- train_batch_size: 10
- eval_batch_size: 10
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 127  | 0.7652          |
| No log        | 2.0   | 254  | 0.7520          |
| No log        | 3.0   | 381  | 0.7681          |
| 0.9618        | 4.0   | 508  | 0.7337          |
| 0.9618        | 5.0   | 635  | 0.7560          |
| 0.9618        | 6.0   | 762  | 0.7397          |
| 0.9618        | 7.0   | 889  | 0.7298          |
| 0.6652        | 8.0   | 1016 | 0.7891          |
| 0.6652        | 9.0   | 1143 | 0.7874          |
| 0.6652        | 10.0  | 1270 | 0.7759          |
| 0.6652        | 11.0  | 1397 | 0.7505          |
| 0.6174        | 12.0  | 1524 | 0.7838          |
| 0.6174        | 13.0  | 1651 | 0.7878          |
| 0.6174        | 14.0  | 1778 | 0.8028          |
| 0.6174        | 15.0  | 1905 | 0.8154          |
| 0.5733        | 16.0  | 2032 | 0.8131          |
| 0.5733        | 17.0  | 2159 | 0.8278          |
| 0.5733        | 18.0  | 2286 | 0.8308          |
| 0.5733        | 19.0  | 2413 | 0.8433          |
| 0.5378        | 20.0  | 2540 | 0.8303          |
| 0.5378        | 21.0  | 2667 | 0.8352          |
| 0.5378        | 22.0  | 2794 | 0.8369          |
| 0.5378        | 23.0  | 2921 | 0.8518          |
| 0.5095        | 24.0  | 3048 | 0.8749          |
| 0.5095        | 25.0  | 3175 | 0.8533          |
| 0.5095        | 26.0  | 3302 | 0.8547          |
| 0.5095        | 27.0  | 3429 | 0.8844          |
| 0.4856        | 28.0  | 3556 | 0.8752          |
| 0.4856        | 29.0  | 3683 | 0.8804          |
| 0.4856        | 30.0  | 3810 | 0.8801          |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.0
- Datasets 1.11.0
- Tokenizers 0.10.3
