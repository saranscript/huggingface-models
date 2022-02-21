---
language:
- en
license: mit
widget:
- text: "She was badly wounded already. Another spear would take her down."
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: deberta-v3-large-mnli-2
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE MNLI
      type: glue
      args: mnli
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.8949349064279902
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# DeBERTa-v3-large fine-tuned on MNLI

This model is a fine-tuned version of [microsoft/deberta-v3-large](https://huggingface.co/microsoft/deberta-v3-large) on the GLUE MNLI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6763
- Accuracy: 0.8949

## Model description

[DeBERTa](https://arxiv.org/abs/2006.03654) improves the BERT and RoBERTa models using disentangled attention and enhanced mask decoder. With those two improvements, DeBERTa out perform RoBERTa on a majority of NLU tasks with 80GB training data. 

In [DeBERTa V3](https://arxiv.org/abs/2111.09543), we further improved the efficiency of DeBERTa using ELECTRA-Style pre-training with Gradient Disentangled Embedding Sharing. Compared to DeBERTa,  our V3 version significantly improves the model performance on downstream tasks.  You can find more technique details about the new model from our [paper](https://arxiv.org/abs/2111.09543).

Please check the [official repository](https://github.com/microsoft/DeBERTa) for more implementation details and updates.

The DeBERTa V3 large model comes with 24 layers and a hidden size of 1024. It has 304M backbone parameters  with a vocabulary containing 128K tokens which introduces 131M parameters in the Embedding layer.  This model was trained using the 160GB data as DeBERTa V2.

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

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
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Accuracy |
|:-------------:|:-----:|:------:|:---------------:|:--------:|
| 0.3676        | 1.0   | 24544  | 0.3761          | 0.8681   |
| 0.2782        | 2.0   | 49088  | 0.3605          | 0.8881   |
| 0.1986        | 3.0   | 73632  | 0.4672          | 0.8894   |
| 0.1299        | 4.0   | 98176  | 0.5248          | 0.8967   |
| 0.0643        | 5.0   | 122720 | 0.6489          | 0.8999   |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
