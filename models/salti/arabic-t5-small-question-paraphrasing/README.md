---
language: 
- ar
tags:
- question-paraphrasing
widget:
- text: "أعد صياغة: ما عدد حروف اللغة العربية؟"
metrics:
- sacrebleu
- rouge
- meteor

---

# Arabic T5v1.1 for question paraphrasing

This is a fine-tuned [arabic-t5-small](https://huggingface.co/flax-community/arabic-t5-small) on the task of question paraphrasing.

A demo of the trained model using HF Spaces can be found [here](https://huggingface.co/spaces/salti/arabic-question-paraphrasing)

## Training data

The model was fine-tuned using the [Semantic Question Similarity in Arabic](https://www.kaggle.com/c/nsurl-2019-task8/data) data on kaggle.

Only the rows of the dataset where the label is `True` (the two questions have the same meaning) were taken.

The training data was then also mirrored; so if `q1` and `q2` were two questions with the same meaning, then `(q1, q2)` and `(q2, q1)` were both present in the training set. The evaluation set was kept unmirrored of course.

## Training config

|                 |          |
| :-------------: | :------: |
|  `batch size`   |   128    |
| `dropout rate`  |   0.1    |
| `learning rate` |  0.001   |
|  `lr schedule`  | constant |
| `weight decay`  |   1e-7   |
|    `epochs`     |    3     |

## Results

|                   |        |
| :---------------: | :----: |
|  `training loss`  | 0.7086 |
| `evaluation loss` | 0.9819 |
|     `meteor`      | 49.277 |
|   `sacreBLEU-1`   | 57.088 |
|   `sacreBLEU-2`   | 39.846 |
|   `sacreBLEU-3`   | 29.444 |
|   `sacreBLEU-4`   | 22.601 |
|  `Rouge F1 max`   | 1.299  |
