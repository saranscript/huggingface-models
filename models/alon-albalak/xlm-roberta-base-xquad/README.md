---
tags:
- multilingual
datasets:
- xquad
---
# xlm-roberta-base for multilingual QA
# Overview
**Language Model**: xlm-roberta-base \
**Downstream task**: Extractive QA \
**Training data**: [XQuAD](https://github.com/deepmind/xquad)\
**Testing Data**: [XQuAD](https://github.com/deepmind/xquad)

# Hyperparameters
```python
batch_size = 40
n_epochs = 10
max_seq_len = 384
doc_stride = 128
learning_rate = 3e-5
```
# Performance
Evaluated on held-out test set from XQuAD
```python
"exact_match": 79.44756554307116,
"f1": 89.79318021513376,
"test_samples": 2307
```

# Usage

## In Transformers
```python
from transformers import AutoModelForQuestionAnswering, AutoTokenizer, pipeline

model_name = "alon-albalak/xlm-roberta-base-xquad"

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

model_name = "alon-albalak/xlm-roberta-base-xquad"

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
reader = FARMReader(model_name_or_path="alon-albalak/xlm-roberta-base-xquad")
# or 
reader = TransformersReader(model="alon-albalak/xlm-roberta-base-xquad",tokenizer="alon-albalak/xlm-roberta-base-xquad")
```

Usage instructions for FARM and Haystack were adopted from https://huggingface.co/deepset/xlm-roberta-large-squad2