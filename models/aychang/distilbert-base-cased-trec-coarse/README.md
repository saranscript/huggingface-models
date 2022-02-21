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

# TREC 6-class Task: distilbert-base-cased 

## Model description

A simple base distilBERT model trained on the "trec" dataset.

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

model_name = "aychang/distilbert-base-cased-trec-coarse"

nlp = pipeline("sentiment-analysis", model=model_name, tokenizer=model_name)

results = nlp(["Where did the queen go?", "Why did the Queen hire 1000 ML Engineers?"])
```

##### AdaptNLP

```python
from adaptnlp import EasySequenceClassifier

model_name = "aychang/distilbert-base-cased-trec-coarse"
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
    overwrite_output_dir=False,
    num_train_epochs=2,
    per_device_train_batch_size=16,
    per_device_eval_batch_size=16,
    warmup_steps=500,
    weight_decay=0.01,
    evaluation_strategy="steps",
    logging_dir='./logs',
    fp16=False,
    eval_steps=500,
    save_steps=300000
)
```

## Eval results

```
{'epoch': 2.0,
 'eval_accuracy': 0.97,
 'eval_f1': array([0.98220641, 0.91620112, 1.        , 0.97709924, 0.98678414,
        0.97560976]),
 'eval_loss': 0.14275787770748138,
 'eval_precision': array([0.96503497, 0.96470588, 1.        , 0.96969697, 0.98245614,
        0.96385542]),
 'eval_recall': array([1.        , 0.87234043, 1.        , 0.98461538, 0.99115044,
        0.98765432]),
 'eval_runtime': 0.9731,
 'eval_samples_per_second': 513.798}
```
