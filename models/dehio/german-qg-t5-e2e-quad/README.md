---
license: mit
widget:
- text: "Naturschutzwarte haben auf der ostfriesischen Insel Wangerooge zwei seltene Kurzschnäuzige Seepferdchen entdeckt. Die Tiere seien vergangene Woche bei einer sogenannten Spülsaumkontrolle entdeckt worden, bei der die Strände eigentlich nach Müll und toten Vögeln abgesucht würden, sagte der Geschäftsführer der zuständigen Naturschutz- und Forschungsgemeinschaft Mellumrat, Mathias Heckroth. Dabei seien den Naturschützern am Nordstrand kurz hintereinander die beiden leblosen, nur wenige Zentimeter großen Tiere aufgefallen. Experten der Nationalparkverwaltung bestimmten beide Tiere als Kurzschnäuzige Seepferdchen (Hippocampus hippocampus)."
inference:
  parameters:
    max_length: 128
language:
- de
tags:
- question generation
datasets:
- deepset/germanquad
model-index:
- name: german-qg-t5-e2e-quad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# german-qg-t5-e2e-quad (Work in progress)

This model is a end-to-end question generation model in German. Given a text, it generates several questions about it. This model is a fine-tuned version of [valhalla/t5-base-e2e-qg](https://huggingface.co/valhalla/t5-base-e2e-qg) on the [GermanQuAD dataset from deepset](https://huggingface.co/datasets/deepset/germanquad).

## Model description 

More information needed

## Training and evaluation data

Bleu_1: 0.196051  
Bleu_2: 0.122380  
Bleu_3: 0.079980  
Bleu_4: 0.053672  

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0

### Training results



### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
