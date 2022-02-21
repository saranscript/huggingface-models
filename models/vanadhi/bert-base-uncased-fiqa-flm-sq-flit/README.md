---
tags:
- generated_from_trainer
model-index:
- name: bert-base-uncased-fiqa-flm-sq-flit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-fiqa-flm-sq-flit


This model is a fine-tuned version of bert-base-uncased on a custom dataset created for question answering in 
financial domain.

## Model description

BERT is a transformers model pretrained on a large corpus of English data in a self-supervised fashion. 
The model was further processed as below for the specific downstream QA task.
1. Pretrained for domain adaptation with Masked language modeling (MLM) objective with
the FIQA challenge Opinion-based QA task is available here - https://drive.google.com/file/d/1BlWaV-qVPfpGyJoWQJU9bXQgWCATgxEP/view
2. Pretrained with MLM objective with custom generated dataset for Banking and Finance.
3. Fine Tuned with SQuAD V2 dataset for QA task adaptation.
4. Fine Tuned with custom labeled dataset in SQuAD format for domain and task adaptation.

## Intended uses & limitations

The model is intended to be used for a custom Questions Answering system in the BFSI domain.

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.2
- num_epochs: 2.0

### Training results



### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
