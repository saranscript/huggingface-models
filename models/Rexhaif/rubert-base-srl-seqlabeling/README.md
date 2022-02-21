---
tags:
- generated_from_trainer
model-index:
- name: rubert-base-srl-seqlabeling
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# rubert-base-srl-seqlabeling

This model is a fine-tuned version of [./ruBert-base/](https://huggingface.co/./ruBert-base/) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1537
- Causator Precision: 0.7677
- Causator Recall: 0.8352
- Causator F1: 0.8
- Causator Number: 91
- Expiriencer Precision: 0.9048
- Expiriencer Recall: 0.9694
- Expiriencer F1: 0.9360
- Expiriencer Number: 98
- Instrument Precision: 0.6
- Instrument Recall: 1.0
- Instrument F1: 0.7500
- Instrument Number: 6
- Other Precision: 0.0
- Other Recall: 0.0
- Other F1: 0.0
- Other Number: 1
- Predicate Precision: 0.9137
- Predicate Recall: 0.9845
- Predicate F1: 0.9478
- Predicate Number: 129
- Overall Precision: 0.8612
- Overall Recall: 0.9354
- Overall F1: 0.8968
- Overall Accuracy: 0.9661

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.98) and epsilon=1e-06
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.06
- num_epochs: 10.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Causator Precision | Causator Recall | Causator F1 | Causator Number | Expiriencer Precision | Expiriencer Recall | Expiriencer F1 | Expiriencer Number | Instrument Precision | Instrument Recall | Instrument F1 | Instrument Number | Other Precision | Other Recall | Other F1 | Other Number | Predicate Precision | Predicate Recall | Predicate F1 | Predicate Number | Overall Precision | Overall Recall | Overall F1 | Overall Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:------------------:|:---------------:|:-----------:|:---------------:|:---------------------:|:------------------:|:--------------:|:------------------:|:--------------------:|:-----------------:|:-------------:|:-----------------:|:---------------:|:------------:|:--------:|:------------:|:-------------------:|:----------------:|:------------:|:----------------:|:-----------------:|:--------------:|:----------:|:----------------:|
| 0.3043        | 1.0   | 56   | 0.3538          | 0.75               | 0.6264          | 0.6826      | 91              | 0.7981                | 0.8469             | 0.8218         | 98                 | 0.0                  | 0.0               | 0.0           | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.8741              | 0.9690           | 0.9191       | 129              | 0.8204            | 0.8154         | 0.8179     | 0.9142           |
| 0.2664        | 2.0   | 112  | 0.1961          | 0.8784             | 0.7143          | 0.7879      | 91              | 0.9175                | 0.9082             | 0.9128         | 98                 | 0.6                  | 1.0               | 0.7500        | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9398              | 0.9690           | 0.9542       | 129              | 0.9076            | 0.8769         | 0.8920     | 0.9399           |
| 0.0373        | 3.0   | 168  | 0.1275          | 0.8706             | 0.8132          | 0.8409      | 91              | 0.9223                | 0.9694             | 0.9453         | 98                 | 0.625                | 0.8333            | 0.7143        | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9338              | 0.9845           | 0.9585       | 129              | 0.9066            | 0.9262         | 0.9163     | 0.9641           |
| 0.0496        | 4.0   | 224  | 0.1683          | 0.8                | 0.8352          | 0.8172      | 91              | 0.9143                | 0.9796             | 0.9458         | 98                 | 0.6667               | 1.0               | 0.8           | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9270              | 0.9845           | 0.9549       | 129              | 0.8815            | 0.9385         | 0.9091     | 0.9608           |
| 0.0529        | 5.0   | 280  | 0.1526          | 0.7917             | 0.8352          | 0.8128      | 91              | 0.8991                | 1.0                | 0.9469         | 98                 | 0.6                  | 1.0               | 0.7500        | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9203              | 0.9845           | 0.9513       | 129              | 0.8697            | 0.9446         | 0.9056     | 0.9627           |
| 0.0419        | 6.0   | 336  | 0.1402          | 0.7755             | 0.8352          | 0.8042      | 91              | 0.8962                | 0.9694             | 0.9314         | 98                 | 0.6                  | 1.0               | 0.7500        | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9203              | 0.9845           | 0.9513       | 129              | 0.8636            | 0.9354         | 0.8981     | 0.9651           |
| 0.0156        | 7.0   | 392  | 0.1498          | 0.8105             | 0.8462          | 0.8280      | 91              | 0.9048                | 0.9694             | 0.9360         | 98                 | 0.6                  | 1.0               | 0.7500        | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9137              | 0.9845           | 0.9478       | 129              | 0.8739            | 0.9385         | 0.9050     | 0.9661           |
| 0.0066        | 8.0   | 448  | 0.1509          | 0.7835             | 0.8352          | 0.8085      | 91              | 0.9057                | 0.9796             | 0.9412         | 98                 | 0.6                  | 1.0               | 0.7500        | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9137              | 0.9845           | 0.9478       | 129              | 0.8665            | 0.9385         | 0.9010     | 0.9680           |
| 0.0084        | 9.0   | 504  | 0.1548          | 0.7755             | 0.8352          | 0.8042      | 91              | 0.9048                | 0.9694             | 0.9360         | 98                 | 0.6                  | 1.0               | 0.7500        | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9137              | 0.9845           | 0.9478       | 129              | 0.8636            | 0.9354         | 0.8981     | 0.9656           |
| 0.0083        | 10.0  | 560  | 0.1537          | 0.7677             | 0.8352          | 0.8         | 91              | 0.9048                | 0.9694             | 0.9360         | 98                 | 0.6                  | 1.0               | 0.7500        | 6                 | 0.0             | 0.0          | 0.0      | 1            | 0.9137              | 0.9845           | 0.9478       | 129              | 0.8612            | 0.9354         | 0.8968     | 0.9661           |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
