---
tags:
- multilingual
datasets:
- xquad
---

# bert-base-multilingual-uncased for multilingual QA

# Overview
**Language Model**: bert-base-multilingual-uncased \
**Downstream task**: Extractive QA \
**Training data**: [XQuAD](https://github.com/deepmind/xquad) \
**Testing Data**: [XQuAD](https://github.com/deepmind/xquad)

# Hyperparameters

```python
batch_size = 48
n_epochs = 6
max_seq_len = 384
doc_stride = 128
learning_rate = 3e-5
```

# Performance

Evaluated on held-out test set from XQuAD
```python
"exact_match": 64.6067415730337,
"f1": 79.52043478874286,
"test_samples": 2384
```

# Usage

## In Transformers
```python
from transformers import AutoModelForQuestionAnswering, AutoTokenizer, pipeline

model_name = "alon-albalak/bert-base-multilingual-xquad"

# a) Get predictions
nlp = pipeline('question-answering', model=model_name, tokenizer=model_name)
QA_input = {
    'question': 'Why is model conversion important?',
    'context': 'The option to convert models between FARM and transformers gives freedom to the user and let people easily switch between frameworks.'
}
res = nlp(QA_input)

# b) Load model & tokenizer
model = AutoModelForQuestionAnswering.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)
```

## In FARM
```python
from farm.modeling.adaptive_model import AdaptiveModel
from farm.modeling.tokenization import Tokenizer
from farm.infer import QAInferencer

model_name = "alon-albalak/bert-base-multilingual-xquad"

# a) Get predictions
nlp = QAInferencer.load(model_name)
QA_input = [{"questions": ["Why is model conversion important?"],
             "text": "The option to convert models between FARM and transformers gives freedom to the user and let people easily switch between frameworks."}]
res = nlp.inference_from_dicts(dicts=QA_input, rest_api_schema=True)

# b) Load model & tokenizer
model = AdaptiveModel.convert_from_transformers(model_name, device="cpu", task_type="question_answering")
tokenizer = Tokenizer.load(model_name)
```

## In Haystack

```python
reader = FARMReader(model_name_or_path="alon-albalak/bert-base-multilingual-xquad")
# or 
reader = TransformersReader(model="alon-albalak/bert-base-multilingual-xquad",tokenizer="alon-albalak/bert-base-multilingual-xquad")
```

Usage instructions for FARM and Haystack were adopted from https://huggingface.co/deepset/xlm-roberta-large-squad2