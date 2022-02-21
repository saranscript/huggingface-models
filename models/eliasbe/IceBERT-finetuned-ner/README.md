---
license: gpl-3.0
tags:
- generated_from_trainer
datasets:
- mim_gold_ner
model-index:
- name: IceBERT-finetuned-ner
widget:
- text: systurnar guðrún og monique voru einar í skóginum umkringdar víði, eik og reyni með þá ósk að sameinast fjölskyldu sinni sem fór á mai thai og í bíó paradís að sjá jim carey leika í the eternal sunshine of the spotless mind.
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# IceBERT-finetuned-ner

This model is a fine-tuned version of [eliasbe/IceBERT-finetuned-ner](https://huggingface.co/eliasbe/IceBERT-finetuned-ner) on the mim_gold_ner dataset.

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Framework versions

- Transformers 4.11.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
