---
license: apache-2.0
tags:
- generated_from_trainer
- sibyl
datasets:
- dbpedia_14
metrics:
- accuracy
model-index:
- name: bert-base-uncased-dbpedia_14
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: dbpedia_14
      type: dbpedia_14
      args: dbpedia_14
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9902857142857143
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-dbpedia_14

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the dbpedia_14 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0547
- Accuracy: 0.9903

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
- lr_scheduler_warmup_steps: 34650
- training_steps: 346500

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 1.7757        | 0.03  | 2000  | 0.2732          | 0.9880   |
| 0.1002        | 0.06  | 4000  | 0.0620          | 0.9891   |
| 0.0547        | 0.09  | 6000  | 0.0723          | 0.9879   |
| 0.0558        | 0.12  | 8000  | 0.0678          | 0.9875   |
| 0.0534        | 0.14  | 10000 | 0.0554          | 0.9896   |
| 0.0632        | 0.17  | 12000 | 0.0670          | 0.9888   |
| 0.0612        | 0.2   | 14000 | 0.0733          | 0.9873   |
| 0.0667        | 0.23  | 16000 | 0.0623          | 0.9896   |
| 0.0636        | 0.26  | 18000 | 0.0836          | 0.9868   |
| 0.0705        | 0.29  | 20000 | 0.0776          | 0.9855   |
| 0.0726        | 0.32  | 22000 | 0.0805          | 0.9861   |
| 0.0778        | 0.35  | 24000 | 0.0713          | 0.9870   |
| 0.0713        | 0.38  | 26000 | 0.1277          | 0.9805   |
| 0.0965        | 0.4   | 28000 | 0.0810          | 0.9855   |
| 0.0881        | 0.43  | 30000 | 0.0910          | 0.985    |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1
- Datasets 1.6.1
- Tokenizers 0.10.3
