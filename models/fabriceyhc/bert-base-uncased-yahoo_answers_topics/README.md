---
license: apache-2.0
tags:
- generated_from_trainer
- sibyl
datasets:
- yahoo_answers_topics
metrics:
- accuracy
model-index:
- name: bert-base-uncased-yahoo_answers_topics
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: yahoo_answers_topics
      type: yahoo_answers_topics
      args: yahoo_answers_topics
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.7499166666666667
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-yahoo_answers_topics

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the yahoo_answers_topics dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8092
- Accuracy: 0.7499

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
- train_batch_size: 8
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 86625
- training_steps: 866250

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 2.162         | 0.01  | 2000  | 1.7444          | 0.5681   |
| 1.3126        | 0.02  | 4000  | 1.0081          | 0.7054   |
| 0.9592        | 0.03  | 6000  | 0.9021          | 0.7234   |
| 0.8903        | 0.05  | 8000  | 0.8827          | 0.7276   |
| 0.8685        | 0.06  | 10000 | 0.8540          | 0.7341   |
| 0.8422        | 0.07  | 12000 | 0.8547          | 0.7365   |
| 0.8535        | 0.08  | 14000 | 0.8264          | 0.7372   |
| 0.8178        | 0.09  | 16000 | 0.8331          | 0.7389   |
| 0.8325        | 0.1   | 18000 | 0.8242          | 0.7411   |
| 0.8181        | 0.12  | 20000 | 0.8356          | 0.7437   |
| 0.8171        | 0.13  | 22000 | 0.8090          | 0.7451   |
| 0.8092        | 0.14  | 24000 | 0.8469          | 0.7392   |
| 0.8057        | 0.15  | 26000 | 0.8185          | 0.7478   |
| 0.8085        | 0.16  | 28000 | 0.8090          | 0.7467   |
| 0.8229        | 0.17  | 30000 | 0.8225          | 0.7417   |
| 0.8151        | 0.18  | 32000 | 0.8262          | 0.7419   |
| 0.81          | 0.2   | 34000 | 0.8149          | 0.7383   |
| 0.8073        | 0.21  | 36000 | 0.8225          | 0.7441   |
| 0.816         | 0.22  | 38000 | 0.8037          | 0.744    |
| 0.8217        | 0.23  | 40000 | 0.8409          | 0.743    |
| 0.82          | 0.24  | 42000 | 0.8286          | 0.7385   |
| 0.8101        | 0.25  | 44000 | 0.8282          | 0.7413   |
| 0.8254        | 0.27  | 46000 | 0.8170          | 0.7414   |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1
- Datasets 1.6.1
- Tokenizers 0.10.3
