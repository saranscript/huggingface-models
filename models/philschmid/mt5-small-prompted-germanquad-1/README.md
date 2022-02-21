---
license: apache-2.0
tags:
- summarization
datasets:
- philschmid/prompted-germanquad
widget:
 - text: |
     Philipp ist 26 Jahre alt und lebt in Nürnberg, Deutschland. Derzeit arbeitet er als Machine Learning Engineer und Tech Lead bei Hugging Face, um künstliche Intelligenz durch Open Source und Open Science zu demokratisieren.
     
     Welches Ziel hat Hugging Face?
metrics:
- rouge
model-index:
- name: mt5-small-prompted-germanquad-1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-small-prompted-germanquad-1

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on an [philschmid/prompted-germanquad](https://huggingface.co/datasets/philschmid/prompted-germanquad) dataset. A prompt datasets using the [BigScience PromptSource library](https://github.com/bigscience-workshop/promptsource). The dataset is a copy of [germanquad](https://huggingface.co/datasets/deepset/germanquad) with applying the  `squad` template and translated it to german. [TEMPLATE](https://github.com/philschmid/promptsource/blob/main/promptsource/templates/germanquad/templates.yaml).

This is a first test if it is possible to fine-tune `mt5` models to solve similar tasks than `T0` of big science but for the German language.

It achieves the following results on the evaluation set:
- Loss: 1.6835
- Rouge1: 27.7309
- Rouge2: 18.7311
- Rougel: 27.4704
- Rougelsum: 27.4818

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5.6e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 7

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum |
|:-------------:|:-----:|:------:|:---------------:|:-------:|:-------:|:-------:|:---------:|
| 3.3795        | 1.0   | 17496  | 2.0693          | 15.8652 | 9.2569  | 15.6237 | 15.6142   |
| 2.3582        | 2.0   | 34992  | 1.9057          | 21.9348 | 14.0057 | 21.6769 | 21.6825   |
| 2.1809        | 3.0   | 52488  | 1.8143          | 24.3401 | 16.0354 | 24.0862 | 24.0914   |
| 2.0721        | 4.0   | 69984  | 1.7563          | 25.8672 | 17.2442 | 25.5854 | 25.6051   |
| 2.0004        | 5.0   | 87480  | 1.7152          | 27.0275 | 18.0548 | 26.7561 | 26.7685   |
| 1.9531        | 6.0   | 104976 | 1.6939          | 27.4702 | 18.5156 | 27.2027 | 27.2107   |
| 1.9218        | 7.0   | 122472 | 1.6835          | 27.7309 | 18.7311 | 27.4704 | 27.4818   |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.1+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
