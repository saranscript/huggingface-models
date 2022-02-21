---
license: mit
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: punct_restore_fr
  results:
  - task:
      name: Token Classification
      type: token-classification
    metric:
      name: Accuracy
      type: accuracy
      value: 0.991500810518732
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# punct_restore_fr

This model is a fine-tuned version of [camembert-base](https://huggingface.co/camembert-base) on a raw, French opensubtitles dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0301
- Precision: 0.9601
- Recall: 0.9527
- F1: 0.9564
- Accuracy: 0.9915

## Model description

Classifies tokens based on beginning of French sentences (B-SENT) and everything else (O).

## Intended uses & limitations

This model aims to help punctuation restoration on French YouTube auto-generated subtitles. In doing so, one can measure more in a corpus such as words per sentence, grammar structures per sentence, etc.
 
## Training and evaluation data

1 million Open Subtitles (French) sentences. 80%/10%/10% training/validation/test split.

The sentences:

- were lower-cased
- had end punctuation (.?!) removed
- were of length between 7 and 70 words
- had beginning word of sentence tagged with B-SENT.
    - All other words marked with O.

Token/tag pairs batched together in groups of 64. This helps show variety of positions for B-SENT and O tags. This also keeps training examples from just being one sentence. Otherwise, this leads to having the first word and only the first word in a sequence being labeled B-SENT.

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 1
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results



### Framework versions

- Transformers 4.8.1
- Pytorch 1.9.0+cu102
- Datasets 1.8.0
- Tokenizers 0.10.3
