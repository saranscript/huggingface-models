---
license: mit
tags:
- generated_from_trainer
model-index:
- name: gpt2-finetuned-scientific-articles
  results: []
---

This repository is the submission for the final project for BF510 [Institutional Racism in Health and Science](http://irhs.bu.edu/) for Shariq Madha.

To see Jupyter detailing how this model was produced, as well as the motivation behind it, go [here](https://github.com/ssmadha/BF510-final-project/).

To try this out yourself, enter a prompt in the textbox to the right and hit compute (it may take a minute for the first to process, but subsequent results should be quick).

# gpt2-finetuned-scientific-articles

This model is a fine-tuned version of [gpt2](https://huggingface.co/gpt2) on scientific articles about algorithmic bias.
It achieves the following results on the evaluation set:
- Loss: 2.3793

## Model description

This model is a casual language modeling GPT2 fine-tuned on scientific articles about algorithmic bias, in an attempt to showcase an example about correcting for algorithmic bias.

## Intended uses & limitations

This model is intended for prompts about algorithms and bias. Other prompts will yield results, but they are less likely to be influenced by the fine-tuning.

## Training and evaluation data

This model is trained on fully freely accessible articles obtained from a PubMed Central search on algorithmic bias. The pmc_result_algorithmicbias.txt file contains the list of PMC's used. Due to technical and time limitations, only fine-tuned on the introduction sections, but training on other sections is planned.

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.5293        | 1.0   | 1071 | 2.3892          |
| 2.4821        | 2.0   | 2142 | 2.3793          |


### Framework versions

- Transformers 4.14.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
