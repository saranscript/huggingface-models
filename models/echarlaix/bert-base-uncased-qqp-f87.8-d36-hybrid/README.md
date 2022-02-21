---
language: en
license: apache-2.0
tags:
- text-classification 
datasets:
- qqp
metrics:
- F1
---

## bert-base-uncased model fine-tuned on QQP

This model was created using the [nn_pruning](https://github.com/huggingface/nn_pruning) python library: the linear layers contains **36%** of the original  weights.


The model contains **50%** of the original weights **overall** (the embeddings account for a significant part of the model, and they are not pruned by this method).


<div class="graph"><script src="/echarlaix/bert-base-uncased-qqp-f87.8-d36-hybrid/raw/main/model_card/density_info.js" id="70162e64-2a82-4147-ac7a-864cfe18a013"></script></div>


## Fine-Pruning details
This model was fine-tuned from the HuggingFace [model](https://huggingface.co/bert-base-uncased) checkpoint on task, and distilled from the model [textattack/bert-base-uncased-QQP](https://huggingface.co/textattack/bert-base-uncased-QQP).
This model is case-insensitive: it does not make a difference between english and English.

A side-effect of block pruning is that some of the attention heads are completely removed: 54 heads were removed on a total of 144 (37.5%).

<div class="graph"><script src="/echarlaix/bert-base-uncased-qqp-f87.8-d36-hybrid/raw/main/model_card/pruning_info.js" id="f4fb8229-3e66-406e-b99f-f771ce6117c8"></script></div>

## Details of the QQP dataset

| Dataset  | Split | # samples |
| -------- | ----- | --------- |
|    QQP   | train | 364K      |
|    QQP   | eval  |  40K      |

### Results

**Pytorch model file size**: `377MB` (original BERT: `420MB`)

| Metric | # Value   | 
| ------ | --------- | 
| **F1** | **87.87** | 



