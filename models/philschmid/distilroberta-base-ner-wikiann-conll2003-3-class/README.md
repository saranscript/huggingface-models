---
license: apache-2.0
tags:
- token-classification
datasets:
- wikiann-conll2003
metrics:
- precision
- recall
- f1
- accuracy

model-index:
- name: distilroberta-base-ner-wikiann-conll2003-3-class
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wikiann-conll2003
      type: wikiann-conll2003
    metrics:
      - name: Precision
        type: precision
        value: 0.9624757386241104
      - name: Recall
        type: recall
        value: 0.9667497021553124
      - name: F1
        type: f1
        value: 0.964607986167396
      - name: Accuracy
        type: accuracy
        value: 0.9913626461292995
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilroberta-base-ner-wikiann-conll2003-3-class

This model is a fine-tuned version of [distilroberta-base](https://huggingface.co/distilroberta-base) on the wikiann and conll2003 dataset. It consists out of the classes of wikiann. 

O (0), B-PER (1), I-PER (2), B-ORG (3), I-ORG (4) B-LOC (5), I-LOC (6).

eval F1-Score: **96,25** (merged dataset)   
test F1-Score: **92,41** (merged dataset) 



## Model Usage

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

tokenizer = AutoTokenizer.from_pretrained("philschmid/distilroberta-base-ner-wikiann-conll2003-3-class")
model = AutoModelForTokenClassification.from_pretrained("philschmid/distilroberta-base-ner-wikiann-conll2003-3-class")

nlp = pipeline("ner", model=model, tokenizer=tokenizer, grouped_entities=True)
example = "My name is Philipp and live in Germany"

nlp(example)

```

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 4.9086903597787154e-05
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0
- mixed_precision_training: Native AMP

### Training results

It achieves the following results on the evaluation set:
- Loss: 0.0520
- Precision: 0.9625
- Recall: 0.9667
- F1: 0.9646
- Accuracy: 0.9914

It achieves the following results on the test set:
- Loss: 0.141
- Precision: 0.917
- Recall: 0.9313
- F1: 0.9241
- Accuracy: 0.9807


### Framework versions

- Transformers 4.6.1
- Pytorch 1.8.1+cu101
- Datasets 1.6.2
- Tokenizers 0.10.3
