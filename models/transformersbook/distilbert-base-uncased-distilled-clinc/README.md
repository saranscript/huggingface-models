---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- clinc_oos
metrics:
- accuracy
model-index:
- name: distilbert-base-uncased-distilled-clinc
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: clinc_oos
      type: clinc_oos
      args: plus
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9393548387096774
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-distilled-clinc

This model is a fine-tuned with knowledge distillation version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the clinc_oos dataset. The model is used in Chapter 8: Making Transformers Efficient in Production in the [NLP with Transformers book](https://learning.oreilly.com/library/view/natural-language-processing/9781098103231/). You can find the full code in the accompanying [Github repository](https://github.com/nlp-with-transformers/notebooks/blob/main/08_model-compression.ipynb).

It achieves the following results on the evaluation set:
- Loss: 0.1005
- Accuracy: 0.9394

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 48
- eval_batch_size: 48
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.9031        | 1.0   | 318  | 0.5745          | 0.7365   |
| 0.4481        | 2.0   | 636  | 0.2856          | 0.8748   |
| 0.2528        | 3.0   | 954  | 0.1798          | 0.9187   |
| 0.176         | 4.0   | 1272 | 0.1398          | 0.9294   |
| 0.1416        | 5.0   | 1590 | 0.1211          | 0.9348   |
| 0.1243        | 6.0   | 1908 | 0.1116          | 0.9348   |
| 0.1133        | 7.0   | 2226 | 0.1062          | 0.9377   |
| 0.1075        | 8.0   | 2544 | 0.1035          | 0.9387   |
| 0.1039        | 9.0   | 2862 | 0.1014          | 0.9381   |
| 0.1018        | 10.0  | 3180 | 0.1005          | 0.9394   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1+cu102
- Datasets 1.13.0
- Tokenizers 0.10.3
