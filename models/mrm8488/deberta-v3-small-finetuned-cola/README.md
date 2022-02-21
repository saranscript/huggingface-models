---
language:
- en
license: mit
tags:
- generated_from_trainer
datasets:
- glue
widget:
- text: "They represented seriously to the dean Mary as a genuine linguist."
metrics:
- matthews_correlation
model-index:
- name: deberta-v3-small
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE COLA
      type: glue
      args: cola
    metrics:
    - name: Matthews Correlation
      type: matthews_correlation
      value: 0.6333205721749096
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# DeBERTa-v3-small fine-tuned on CoLA

This model is a fine-tuned version of [microsoft/deberta-v3-small](https://huggingface.co/microsoft/deberta-v3-small) on the GLUE COLA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4051
- Matthews Correlation: 0.6333

## Model description

[DeBERTa](https://arxiv.org/abs/2006.03654) improves the BERT and RoBERTa models using disentangled attention and enhanced mask decoder. With those two improvements, DeBERTa out perform RoBERTa on a majority of NLU tasks with 80GB training data. 

Please check the [official repository](https://github.com/microsoft/DeBERTa) for more details and updates.

In [DeBERTa V3](https://arxiv.org/abs/2111.09543), we replaced the MLM objective with the RTD(Replaced Token Detection) objective introduced by ELECTRA for pre-training, as well as some innovations to be introduced in our upcoming paper. Compared to DeBERTa-V2,  our V3 version significantly improves the model performance in downstream tasks.  You can find a simple introduction about the model from the appendix A11 in our original [paper](https://arxiv.org/abs/2006.03654),  but we will provide more details in a separate write-up.

The DeBERTa V3 small model comes with 6 layers and a hidden size of 768. Its total parameter number is 143M since we use a vocabulary containing 128K tokens which introduce 98M parameters in the Embedding layer.  This model was trained using the 160GB data as DeBERTa V2.

## Intended uses & limitations

More information needed

## Training and evaluation data


The Corpus of Linguistic Acceptability (CoLA) in its full form consists of 10657 sentences from 23 linguistics publications, expertly annotated for acceptability (grammaticality) by their original authors. The public version provided here contains 9594 sentences belonging to training and development sets, and excludes 1063 sentences belonging to a held out test set.


## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Matthews Correlation |
|:-------------:|:-----:|:----:|:---------------:|:--------------------:|
| No log        | 1.0   | 535  | 0.4051          | 0.6333               |
| 0.3371        | 2.0   | 1070 | 0.4455          | 0.6531               |
| 0.3371        | 3.0   | 1605 | 0.5755          | 0.6499               |
| 0.1305        | 4.0   | 2140 | 0.7188          | 0.6553               |
| 0.1305        | 5.0   | 2675 | 0.8047          | 0.6700               |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
