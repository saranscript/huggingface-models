---
language: en
---

# Sparse BERT base model (uncased)

Pretrained model pruned to 1:2 structured sparsity.
The model is a pruned version of the [BERT base model](https://huggingface.co/bert-base-uncased).

## Intended Use

The model can be used for fine-tuning to downstream tasks with sparsity already embeded to the model.
To keep the sparsity a mask should be added to each sparse weight blocking the optimizer from updating the zeros.

## Evaluation Results
We get the following results on the tasks development set, all results are mean of 5 different seeded models:

| Task | MNLI-m (Acc) | MNLI-mm (Acc) | QQP (Acc/F1) | QNLI (Acc) | SST-2 (Acc) | STS-B (Pears/Spear) | SQuADv1.1 (Acc/F1) |
|------|--------------|---------------|--------------|------------|-------------|---------------------|--------------------|
|      | 83.3         | 83.9          |   90.8/87.6  |    90.4    |     91.3    |      88.8/88.3      |      80.5/88.2     |