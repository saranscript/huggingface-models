---
license: cc-by-nc-4.0
tags:
- generated_from_trainer
metrics:
- accuracy
model_index:
  name: wav2vec2-speechcommands-german
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-speechcommands-german

This model is a fine-tuned version of [facebook/wav2vec2-base-10k-voxpopuli-ft-de](https://huggingface.co/facebook/wav2vec2-base-10k-voxpopuli-ft-de) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2481
- Accuracy: 0.9180

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results



### Framework versions

- Transformers 4.9.1
- Pytorch 1.8.1
- Datasets 1.7.0
- Tokenizers 0.10.2
