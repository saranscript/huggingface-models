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

This model was created using the [nn_pruning](https://github.com/huggingface/nn_pruning) python library: the linear layers contains **23%** of the original  weights.



The model contains **45%** of the original weights **overall** (the embeddings account for a significant part of the model, and they are not pruned by this method).

<div class="graph"><script src="/echarlaix/bart-base-cnn-r2-18.7-d23-hybrid/raw/main/model_card/density_info.js" id="4348cd46-05bd-4e27-b565-6693f9e0b03e"></script></div>


## Fine-Pruning details
This model was fine-tuned from the HuggingFace [model](https://huggingface.co/facebook/bart-base).
A side-effect of block pruning is that some of the attention heads are completely removed: 61 heads were removed on a total of 216 (28.2%).

## Details of the CNN/DailyMail dataset

|    Dataset    | Split | # samples |
| ------------- | ----- | --------- |
| CNN/DailyMail | train |   287K    |
| CNN/DailyMail | eval  |    13K    |

### Results


|    Metric   | # Value   |
| ----------- | --------- |
| **Rouge 1** | **41.43** |
| **Rouge 2** | **18.72** |
| **Rouge L** | **38.35** |
