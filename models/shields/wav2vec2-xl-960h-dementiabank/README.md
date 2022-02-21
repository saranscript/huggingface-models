---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-xl-960h-dementiabank
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xl-960h-dementiabank

This model is a fine-tuned version of [facebook/wav2vec2-large-960h](https://huggingface.co/facebook/wav2vec2-large-960h) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3483.2146
- Wer: 0.9860

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.005
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 13934.5266    | 0.31  | 10   | 71265.4531      | 1.0    |
| 13443.6406    | 0.62  | 20   | 69977.6016      | 1.0    |
| 9336.9562     | 0.94  | 30   | 13763.1484      | 0.9843 |
| 2970.977      | 1.25  | 40   | 17587.7656      | 0.9860 |
| 1916.3354     | 1.56  | 50   | 4328.4521       | 1.0    |
| 1417.5775     | 1.88  | 60   | 4486.8071       | 0.9860 |
| 1841.7689     | 2.19  | 70   | 2988.0303       | 1.0    |
| 1355.0265     | 2.5   | 80   | 2972.6094       | 0.9860 |
| 1359.7979     | 2.81  | 90   | 3483.2146       | 0.9860 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
