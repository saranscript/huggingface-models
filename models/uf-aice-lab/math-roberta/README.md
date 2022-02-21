---
language: 
- en
tags:
- nlp
- math learning
- education
license: mit
---
# Math-RoBerta for NLP tasks in math learning environments

This model is fine-tuned RoBERTa-large trained with 8 Nvidia RTX 1080Ti GPUs using 3,000,000 math discussion posts by students and facilitators on Algebra Nation (https://www.mathnation.com/). MathRoBERTa has 24 layers, and 355 million parameters and its published model weights take up to 1.5 gigabytes of disk space. It can potentially provide a good base performance on NLP related tasks (e.g., text classification, semantic search, Q&A) in similar math learning environments.

### Here is how to use it with texts in HuggingFace
```python
from transformers import RobertaTokenizer, RobertaModel
tokenizer = RobertaTokenizer.from_pretrained('uf-aice-lab/math-roberta')
model = RobertaModel.from_pretrained('uf-aice-lab/math-roberta')
text = "Replace me by any text you'd like."
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
```