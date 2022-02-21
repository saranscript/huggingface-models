---
language: en
license: apache-2.0
tags:
- summarization
datasets:
- cnn_dailymail
metrics:
- R1
- R2
- RL
---

## facebook/bart-base model fine-tuned on CNN/DailyMail

This model was created using the [nn_pruning](https://github.com/huggingface/nn_pruning) python library: the linear layers contains **35%** of the original  weights.



The model contains **53%** of the original weights **overall** (the embeddings account for a significant part of the model, and they are not pruned by this method).

<div class="graph"><script src="/echarlaix/bart-base-cnn-r2-19.4-d35-hybrid/raw/main/model_card/density_info.js" id="c0afb977-b30c-485d-ac75-afc874392380"></script></div>

## Fine-Pruning details
This model was fine-tuned from the HuggingFace [model](https://huggingface.co/facebook/bart-base).

A side-effect of the block pruning is that some of the attention heads are completely removed: 38 heads were removed on a total of 216 (17.6%).

## Details of the CNN/DailyMail  dataset

|    Dataset    | Split | # samples |
| ------------- | ----- | --------- |
| CNN/DailyMail | train |   287K    |
| CNN/DailyMail | eval  |    13K    |


### Results

|    Metric   | # Value   | 
| ----------- | --------- |
| **Rouge 1** | **42.18** | 
| **Rouge 2** | **19.44** | 
| **Rouge L** | **39.17** | 
