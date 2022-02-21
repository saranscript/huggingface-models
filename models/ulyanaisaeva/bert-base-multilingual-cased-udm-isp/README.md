---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bert-base-multilingual-cased-udm-isp
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-multilingual-cased-udm-isp

This model is a fine-tuned version of [bert-base-multilingual-cased](https://huggingface.co/bert-base-multilingual-cased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7809

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 60
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 0.9424        | 1.0   | 69   | 0.9407          |
| 0.9365        | 2.0   | 138  | 0.9064          |
| 0.9044        | 3.0   | 207  | 0.9080          |
| 0.8979        | 4.0   | 276  | 0.8868          |
| 0.8863        | 5.0   | 345  | 0.9078          |
| 0.8878        | 6.0   | 414  | 0.9141          |
| 0.881         | 7.0   | 483  | 0.8467          |
| 0.8678        | 8.0   | 552  | 0.8668          |
| 0.8653        | 9.0   | 621  | 0.8453          |
| 0.8693        | 10.0  | 690  | 0.8529          |
| 0.8412        | 11.0  | 759  | 0.8714          |
| 0.8465        | 12.0  | 828  | 0.8176          |
| 0.8455        | 13.0  | 897  | 0.8455          |
| 0.8063        | 14.0  | 966  | 0.8083          |
| 0.7976        | 15.0  | 1035 | 0.7959          |
| 0.7885        | 16.0  | 1104 | 0.8027          |
| 0.783         | 17.0  | 1173 | 0.7803          |
| 0.7901        | 18.0  | 1242 | 0.7950          |
| 0.7825        | 19.0  | 1311 | 0.7957          |
| 0.7723        | 20.0  | 1380 | 0.7701          |
| 0.7842        | 21.0  | 1449 | 0.7723          |
| 0.7811        | 22.0  | 1518 | 0.8188          |
| 0.7778        | 23.0  | 1587 | 0.7607          |
| 0.7654        | 24.0  | 1656 | 0.7598          |
| 0.7634        | 25.0  | 1725 | 0.8006          |
| 0.7563        | 26.0  | 1794 | 0.7893          |
| 0.7649        | 27.0  | 1863 | 0.7768          |
| 0.7536        | 28.0  | 1932 | 0.7652          |
| 0.7553        | 29.0  | 2001 | 0.7724          |
| 0.761         | 30.0  | 2070 | 0.7378          |
| 0.7445        | 31.0  | 2139 | 0.7420          |
| 0.746         | 32.0  | 2208 | 0.7328          |
| 0.7514        | 33.0  | 2277 | 0.7521          |
| 0.7524        | 34.0  | 2346 | 0.7517          |
| 0.7372        | 35.0  | 2415 | 0.7951          |
| 0.7412        | 36.0  | 2484 | 0.7602          |
| 0.7388        | 37.0  | 2553 | 0.7591          |
| 0.7279        | 38.0  | 2622 | 0.7750          |
| 0.732         | 39.0  | 2691 | 0.7798          |
| 0.7214        | 40.0  | 2760 | 0.7868          |
| 0.7448        | 41.0  | 2829 | 0.7685          |
| 0.7376        | 42.0  | 2898 | 0.7550          |
| 0.7252        | 43.0  | 2967 | 0.7551          |
| 0.7273        | 44.0  | 3036 | 0.7698          |
| 0.7299        | 45.0  | 3105 | 0.7520          |
| 0.7281        | 46.0  | 3174 | 0.7701          |
| 0.7332        | 47.0  | 3243 | 0.7804          |
| 0.7189        | 48.0  | 3312 | 0.7922          |
| 0.7236        | 49.0  | 3381 | 0.7577          |
| 0.7198        | 50.0  | 3450 | 0.7720          |
| 0.7198        | 51.0  | 3519 | 0.7733          |
| 0.7243        | 52.0  | 3588 | 0.7847          |
| 0.7262        | 53.0  | 3657 | 0.7569          |
| 0.7105        | 54.0  | 3726 | 0.8025          |
| 0.7153        | 55.0  | 3795 | 0.7617          |
| 0.723         | 56.0  | 3864 | 0.7693          |
| 0.7134        | 57.0  | 3933 | 0.7405          |
| 0.7243        | 58.0  | 4002 | 0.7860          |
| 0.7196        | 59.0  | 4071 | 0.7629          |
| 0.7173        | 60.0  | 4140 | 0.7809          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Tokenizers 0.11.0
