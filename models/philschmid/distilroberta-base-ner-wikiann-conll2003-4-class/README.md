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
- name: distilroberta-base-ner-wikiann-conll2003-4-class
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
        value: 0.9492143658810326
      - name: Recall
        type: recall
        value: 0.9585379675103891
      - name: F1
        type: f1
        value: 0.9538533834586467
      - name: Accuracy
        type: accuracy
        value: 0.9882022644288301
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilroberta-base-ner-wikiann-conll2003-4-class

This model is a fine-tuned version of [distilroberta-base](https://huggingface.co/distilroberta-base) on the wikiann and conll2003 dataset. It consists out of the classes of conll2003. 

O (0), B-PER (1), I-PER (2), B-ORG (3), I-ORG (4) B-LOC (5), I-LOC (6) B-MISC (7), I-MISC (8).

eval F1-Score: **95,39** (merged dataset)   
test F1-Score: **90,75** (merged dataset) 


## Model Usage

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

tokenizer = AutoTokenizer.from_pretrained("philschmid/distilroberta-base-ner-wikiann-conll2003-4-class")
model = AutoModelForTokenClassification.from_pretrained("philschmid/distilroberta-base-ner-wikiann-conll2003-4-class")

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
- Loss: 0.0705
- Precision: 0.9492
- Recall: 0.9585
- F1: 0.9539
- Accuracy: 0.9882

It achieves the following results on the test set:
- Loss: 0.239
- Precision: 0.8984
- Recall: 0.9168
- F1: 0.9075
- Accuracy: 0.9741



### Framework versions

- Transformers 4.6.1
- Pytorch 1.8.1+cu101
- Datasets 1.6.2
- Tokenizers 0.10.2
