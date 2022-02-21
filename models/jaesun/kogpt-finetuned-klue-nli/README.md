---
license: cc-by-nc-sa-4.0
tags:
- generated_from_trainer
datasets:
- klue
metrics:
- accuracy
model-index:
- name: kogpt-finetuned-klue-nli
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: klue
      type: klue
      args: nli
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.462
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# kogpt-finetuned-klue-nli

This model is a fine-tuned version of [skt/kogpt2-base-v2](https://huggingface.co/skt/kogpt2-base-v2) on the klue dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1329
- Accuracy: 0.462

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 1.0181        | 1.0   | 1375 | 1.0233          | 0.4967   |
| 0.8909        | 2.0   | 2750 | 0.9716          | 0.5157   |
| 0.7243        | 3.0   | 4125 | 1.0293          | 0.5277   |
| 0.4936        | 4.0   | 5500 | 1.2835          | 0.514    |
| 0.3267        | 5.0   | 6875 | 1.9972          | 0.5027   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1
- Datasets 1.14.0
- Tokenizers 0.10.3
