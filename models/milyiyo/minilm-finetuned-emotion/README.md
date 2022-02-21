---
license: mit
tags:
- generated_from_trainer
datasets:
- emotion
metrics:
- f1
model-index:
- name: minilm-finetuned-emotion
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: emotion
      type: emotion
      args: default
    metrics:
    - name: F1
      type: f1
      value: 0.931192
---

Based model: [microsoft/MiniLM-L12-H384-uncased](https://huggingface.co/microsoft/MiniLM-L12-H384-uncased)

Dataset: [emotion](https://huggingface.co/datasets/emotion)

These are the results on the evaluation set:

| Attribute          | Value    |
| ------------------ | -------- |
| Training Loss      | 0.163100 |
| Validation Loss    | 0.192153 |
| F1                 | 0.931192 |
