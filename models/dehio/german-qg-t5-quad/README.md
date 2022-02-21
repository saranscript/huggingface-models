---
license: mit
widget:
- text: "Obwohl die Vereinigten Staaten wie auch viele Staaten des Commonwealth Erben des <hl>britischen Common Laws<hl> sind, setzt sich das amerikanische Recht bedeutend davon ab."
language:
- de
tags:
- question generation
datasets:
- deepset/germanquad
model-index:
- name: german-qg-t5-quad
  results: []
---

# german-qg-t5-quad

This model is fine-tuned in question generation in German. The expected answer must be highlighted with a
&lt;hl> token.

## Task example

#### Input

generate question: Obwohl die Vereinigten Staaten wie auch viele Staaten des Commonwealth Erben des <hl> britischen Common Laws <hl> sind, setzt sich das amerikanische Recht bedeutend davon ab. Dies rührt größtenteils von dem langen Zeitraum her, [...]


#### Expected output

Von welchem Gesetzt stammt das Amerikanische ab? 


## Model description

This model is a fine-tuned version of [valhalla/t5-base-qg-hl](https://huggingface.co/valhalla/t5-base-qg-hl) on the [GermanQUAD](https://www.deepset.ai/germanquad) dataset.

## Training and evaluation data

The training script can be accessed [here](https://github.com/d-e-h-i-o/german-qg).

### Evaluation

The model achieves a BLEU-4 score of **11.30** on the GermanQuAD test set (n=2204). 

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
