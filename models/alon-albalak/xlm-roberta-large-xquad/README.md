---
tags:
- multilingual
datasets:
- xquad
---

# xlm-roberta-large for multilingual QA

# Overview
**Language Model**: xlm-roberta-large \
**Downstream task**: Extractive QA \
**Training data**: [XQuAD](https://github.com/deepmind/xquad) \
**Testing Data**: [XQuAD](https://github.com/deepmind/xquad)

# Hyperparameters

```python
batch_size = 48
n_epochs = 13
max_seq_len = 384
doc_stride = 128
learning_rate = 3e-5
```

# Performance

Evaluated on held-out test set from XQuAD
```python
"exact_match": 87.12546816479401,
"f1": 94.77703248802527,
"test_samples": 2307
```

# Usage

## In Transformers
```python
from transformers import AutoModelForQuestionAnswering, AutoTokenizer, pipeline

model_name = "alon-albalak/xlm-roberta-large-xquad"

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

model_name = "alon-albalak/xlm-roberta-large-xquad"

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
reader = FARMReader(model_name_or_path="alon-albalak/xlm-roberta-large-xquad")
# or 
reader = TransformersReader(model="alon-albalak/xlm-roberta-large-xquad",tokenizer="alon-albalak/xlm-roberta-large-xquad")
```

Usage instructions for FARM and Haystack were adopted from https://huggingface.co/deepset/xlm-roberta-large-squad2