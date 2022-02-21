---
language: ["ru"]
tags:
- russian
- classification
- sentiment
- emotion-classification
- multiclass
datasets:
- cedr
widget:
- text: "Бесишь меня, падла"
- text: "Как здорово, что все мы здесь сегодня собрались"
- text: "Как-то стрёмно, давай свалим отсюда?"
- text: "Грусть-тоска меня съедает"
- text: "Данный фрагмент текста не содержит абсолютно никаких эмоций"
- text: "Нифига себе, неужели так тоже бывает!"

---
This is the [cointegrated/rubert-tiny2](https://huggingface.co/cointegrated/rubert-tiny2) model fine-tuned for classification of emotions in Russian sentences. The task is multilabel classification, because one sentence can contain multiple emotions.

The model on the [CEDR dataset](https://huggingface.co/datasets/cedr) described in the paper ["Data-Driven Model for Emotion Detection in Russian Texts"](https://doi.org/10.1016/j.procs.2021.06.075) by Sboev et al.

The model has been trained with Adam optimizer for 40 epochs with learning rate `1e-5` and batch size 64 [in this notebook](https://colab.research.google.com/drive/1AFW70EJaBn7KZKRClDIdDUpbD46cEsat?usp=sharing).

The quality of the predicted probabilities on the test dataset is the following:

| label    | no emotion | joy    |sadness |surprise| fear   |anger   | mean    | mean (emotions) |
|----------|------------|--------|--------|--------|--------|--------| --------| ----------------|
| AUC      | 0.9286     | 0.9512 | 0.9564 | 0.8908 | 0.8955 | 0.7511 |  0.8956 | 0.8890          |
| F1 micro | 0.8624     | 0.9389 | 0.9362 | 0.9469 | 0.9575 | 0.9261 |  0.9280 | 0.9411          |
| F1 macro | 0.8562     | 0.8962 | 0.9017 | 0.8366 | 0.8359 | 0.6820 |  0.8348 | 0.8305          |
