---
language: 
- nl
tags:
- text-classification
- pytorch
widget:
- text: "Ik heb je lief met heel mijn hart"
  example_title: "Non toxic comment 1"
- text: "Dat is een goed punt, zo had ik het nog niet bekeken."
  example_title: "Non toxic comment 2"
- text: "Wat de fuck zei je net tegen me, klootzak?"
  example_title: "Toxic comment 1"
- text: "Rot op, vuile hoerenzoon."
  example_title: "Toxic comment 2"
license: apache-2.0
metrics:
- Accuracy, F1 Score, Recall, Precision
---
# RobBERT-dutch-base-toxic-comments

## Model description:
This model was created with the purpose to detect toxic or potentially harmful comments.

For this model, we finetuned a dutch RobBerta-based model called [RobBERT](https://huggingface.co/pdelobelle/robbert-v2-dutch-base) on the translated [Jigsaw Toxicity dataset](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge).

The original dataset was translated using the appropriate [MariantMT model](https://huggingface.co/Helsinki-NLP/opus-mt-en-nl).

The model was trained for 2 epochs, on 90% of the dataset, with the following arguments:
```
training_args = TrainingArguments(
    learning_rate=1e-5,
    per_device_train_batch_size=8,
    per_device_eval_batch_size=8,
    gradient_accumulation_steps=6,
    load_best_model_at_end=True,
    metric_for_best_model="recall",
    epochs=2,
    evaluation_strategy="steps",
    save_strategy="steps",
    save_total_limit=10,
    logging_steps=100,
    eval_steps=250,
    save_steps=250,
    weight_decay=0.001,
    report_to="wandb")
```

## Model Performance:

Model evaluation was done on 1/10th of the dataset, which served as the test dataset.

| Accuracy | F1 Score |  Recall  |  Precision  |
| --- | --- | --- | --- |
| 95.63 | 78.80 | 78.99 | 78.61 |

## Dataset:
Unfortunately we cannot open-source the dataset, since we are bound by the underlying Jigsaw license.
