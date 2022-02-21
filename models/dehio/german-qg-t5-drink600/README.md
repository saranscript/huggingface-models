---
license: mit
widget:
- text: "generate question: Der Monk Sour Drink ist ein somit eine aromatische Überraschung, die sowohl <hl>im Sommer wie auch zu Silvester<hl> funktioniert."
language:
- de
tags:
- question generation
datasets:
- deepset/germanquad
model-index:
- name: german-qg-t5-drink600
  results: []
---

# german-qg-t5-drink600

This model is fine-tuned in question generation in German. The expected answer must be highlighted with &lt;hl> token. It is based on [german-qg-t5-quad](https://huggingface.co/dehio/german-qg-t5-quad) and further pre-trained on drink related questions.

## Task example

#### Input

generate question: Der Monk Sour Drink ist ein somit eine aromatische Überraschung, 
die sowohl &lt;hl>im Sommer wie auch zu Silvester&lt;hl> funktioniert.

#### Expected Question
Zu welchen Gelegenheiten passt der Monk Sour gut?

## Model description

The model is based on [german-qg-t5-quad](https://huggingface.co/dehio/german-qg-t5-quad), which was pre-trained on [GermanQUAD](https://www.deepset.ai/germanquad). We further pre-trained it on questions annotated on drink receipts from [Mixology](https://mixology.eu/) ("drink600"). 
We have not yet open sourced the dataset, since we do not own copyright on the source material.

## Training and evaluation data

The training script can be accessed [here](https://github.com/d-e-h-i-o/german-qg).

## Evaluation

It achieves a **BLEU-4 score of 29.80** on the drink600 test set (n=120) and **11.30** on the GermanQUAD test set. 
Thus, fine-tuning on drink600 did not affect performance on GermanQuAD.

In comparison, *german-qg-t5-quad* achieves a BLEU-4 score of **10.76** on the drink600 test set.

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 2
- eval_batch_size: 2
- seed: 100
- gradient_accumulation_steps: 8
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
