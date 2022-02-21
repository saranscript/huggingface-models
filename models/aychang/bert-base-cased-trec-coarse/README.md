---
language: 
- en
thumbnail: 
tags:
- text-classification
license: mit
datasets:
- trec
metrics:
---

# bert-base-cased trained on TREC 6-class task

## Model description

A simple base BERT model trained on the "trec" dataset.

## Intended uses & limitations

#### How to use

##### Transformers

```python
# Load model and tokenizer
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForQuestionAnswering.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)

# Use pipeline
from transformers import pipeline

model_name = "aychang/bert-base-cased-trec-coarse"

nlp = pipeline("sentiment-analysis", model=model_name, tokenizer=model_name)

results = nlp(["Where did the queen go?", "Why did the Queen hire 1000 ML Engineers?"])
```

##### AdaptNLP

```python
from adaptnlp import EasySequenceClassifier

model_name = "aychang/bert-base-cased-trec-coarse"
texts = ["Where did the queen go?", "Why did the Queen hire 1000 ML Engineers?"]

classifer = EasySequenceClassifier
results = classifier.tag_text(text=texts, model_name_or_path=model_name, mini_batch_size=2)
```

#### Limitations and bias

This is minimal language model trained on a benchmark dataset.

## Training data

TREC https://huggingface.co/datasets/trec

## Training procedure

Preprocessing, hardware used, hyperparameters...
#### Hardware
One V100

#### Hyperparameters and Training Args
```python
from transformers import TrainingArguments

training_args = TrainingArguments(
    output_dir='./models',
    num_train_epochs=2,
    per_device_train_batch_size=16,
    per_device_eval_batch_size=16,
    warmup_steps=500,
    weight_decay=0.01,
    evaluation_strategy="steps",
    logging_dir='./logs',
    save_steps=3000
)
```

## Eval results

```
{'epoch': 2.0,
 'eval_accuracy': 0.974,
 'eval_f1': array([0.98181818, 0.94444444, 1.        , 0.99236641, 0.96995708,
        0.98159509]),
 'eval_loss': 0.138086199760437,
 'eval_precision': array([0.98540146, 0.98837209, 1.        , 0.98484848, 0.94166667,
        0.97560976]),
 'eval_recall': array([0.97826087, 0.90425532, 1.        , 1.        , 1.        ,
        0.98765432]),
 'eval_runtime': 1.6132,
 'eval_samples_per_second': 309.943}
```
