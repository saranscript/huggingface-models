---
tags:
- generated_from_trainer
model-index:
  name: wynehills-mimi-ASR
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wynehills-mimi-ASR

This model was trained from scratch on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3822
- Wer: 0.6309

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 70
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 1.54  | 20   | 1.4018          | 0.6435 |
| No log        | 3.08  | 40   | 1.4704          | 0.6593 |
| No log        | 4.62  | 60   | 1.4898          | 0.6625 |
| No log        | 6.15  | 80   | 1.4560          | 0.6404 |
| No log        | 7.69  | 100  | 1.3822          | 0.6309 |
| No log        | 9.23  | 120  | 1.3822          | 0.6309 |
| No log        | 10.77 | 140  | 1.3822          | 0.6309 |
| No log        | 12.31 | 160  | 1.3822          | 0.6309 |
| No log        | 13.85 | 180  | 1.3822          | 0.6309 |
| No log        | 15.38 | 200  | 1.3822          | 0.6309 |
| No log        | 16.92 | 220  | 1.3822          | 0.6309 |
| No log        | 18.46 | 240  | 1.3822          | 0.6309 |
| No log        | 20.0  | 260  | 1.3822          | 0.6309 |
| No log        | 21.54 | 280  | 1.3822          | 0.6309 |
| No log        | 23.08 | 300  | 1.3822          | 0.6309 |
| No log        | 24.62 | 320  | 1.3822          | 0.6309 |
| No log        | 26.15 | 340  | 1.3822          | 0.6309 |
| No log        | 27.69 | 360  | 1.3822          | 0.6309 |
| No log        | 29.23 | 380  | 1.3822          | 0.6309 |
| No log        | 30.77 | 400  | 1.3822          | 0.6309 |
| No log        | 32.31 | 420  | 1.3822          | 0.6309 |
| No log        | 33.85 | 440  | 1.3822          | 0.6309 |
| No log        | 35.38 | 460  | 1.3822          | 0.6309 |
| No log        | 36.92 | 480  | 1.3822          | 0.6309 |
| 0.0918        | 38.46 | 500  | 1.3822          | 0.6309 |
| 0.0918        | 40.0  | 520  | 1.3822          | 0.6309 |
| 0.0918        | 41.54 | 540  | 1.3822          | 0.6309 |
| 0.0918        | 43.08 | 560  | 1.3822          | 0.6309 |
| 0.0918        | 44.62 | 580  | 1.3822          | 0.6309 |
| 0.0918        | 46.15 | 600  | 1.3822          | 0.6309 |
| 0.0918        | 47.69 | 620  | 1.3822          | 0.6309 |
| 0.0918        | 49.23 | 640  | 1.3822          | 0.6309 |
| 0.0918        | 50.77 | 660  | 1.3822          | 0.6309 |
| 0.0918        | 52.31 | 680  | 1.3822          | 0.6309 |
| 0.0918        | 53.85 | 700  | 1.3822          | 0.6309 |
| 0.0918        | 55.38 | 720  | 1.3822          | 0.6309 |
| 0.0918        | 56.92 | 740  | 1.3822          | 0.6309 |
| 0.0918        | 58.46 | 760  | 1.3822          | 0.6309 |
| 0.0918        | 60.0  | 780  | 1.3822          | 0.6309 |
| 0.0918        | 61.54 | 800  | 1.3822          | 0.6309 |
| 0.0918        | 63.08 | 820  | 1.3822          | 0.6309 |
| 0.0918        | 64.62 | 840  | 1.3822          | 0.6309 |
| 0.0918        | 66.15 | 860  | 1.3822          | 0.6309 |
| 0.0918        | 67.69 | 880  | 1.3822          | 0.6309 |
| 0.0918        | 69.23 | 900  | 1.3822          | 0.6309 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
