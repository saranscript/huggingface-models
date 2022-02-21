---

license: apache-2.0

tags:

- token-classification

datasets:

- wikiann

metrics:

- precision

- recall

- f1

- accuracy

model-index:

- name: ner-swedish-wikiann

  results:

  - task:

      name: Token Classification

      type: token-classification

    dataset:

      name: wikiann

      type: wikiann

    metrics:

      - name: Precision

        type: precision

        value: 0.8331921416757433

      - name: Recall

        type: recall

        value: 0.84243586083126

      - name: F1

        type: f1

        value: 0.8377885044416501

      - name: Accuracy

        type: accuracy

        value: 0.91930707459758

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You

should probably proofread and complete it, then remove this comment. -->

# ner-swedish-wikiann

This model is a fine-tuned version of [nordic-roberta-wiki](hhttps://huggingface.co/flax-community/nordic-roberta-wiki) trained for NER on the wikiann dataset.

eval F1-Score: **83,78** 

test F1-Score: **83,76** 

## Model Usage

```python

from transformers import AutoTokenizer, AutoModelForTokenClassification

from transformers import pipeline

tokenizer = AutoTokenizer.from_pretrained("birgermoell/ner-swedish-wikiann")

model = AutoModelForTokenClassification.from_pretrained("birgermoell/ner-swedish-wikiann")

nlp = pipeline("ner", model=model, tokenizer=tokenizer)

example = "Jag heter Per och jag jobbar på KTH"

nlp(example)

```
<!-- 
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

- Loss: 0.3156

- Precision: 0.8332
from transformers import AutoTokenizer, AutoModelForTokenClassification

from transformers import pipeline

tokenizer = AutoTokenizer.from_pretrained("birgermoell/ner-swedish-wikiann")

model = AutoModelForTokenClassification.from_pretrained("birgermoell/ner-swedish-wikiann")

nlp = pipeline("ner", model=model, tokenizer=tokenizer)

example = "Jag heter Per och jag jobbar på KTH"

nlp(example)

- F1: 0.8378

- Accuracy: 0.9193

It achieves the following results on the test set:

- Loss: 0.3023

- Precision: 0.8301

- Recall: 0.8452

- F1: 0.8376

- Accuracy: 0.92

### Framework versions

- Transformers 4.6.1

- Pytorch 1.8.1+cu101

- Datasets 1.6.2

- Tokenizers 0.10.2
 -->
