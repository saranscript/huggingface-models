---
language: en
tags:
- bart
- seq2seq
- summarization
license: apache-2.0
datasets:
- samsum
widget:
- text: | 
    Jeff: Can I train a 🤗 Transformers model on Amazon SageMaker? 
    Philipp: Sure you can use the new Hugging Face Deep Learning Container. 
    Jeff: ok.
    Jeff: and how can I get started? 
    Jeff: where can I find documentation? 
    Philipp: ok, ok you can find everything here. https://huggingface.co/blog/the-partnership-amazon-sagemaker-and-hugging-face
model-index:
- name: bart-base-samsum
  results:
  - task: 
      name: Abstractive Text Summarization
      type: abstractive-text-summarization
    dataset:
      name: "SAMSum Corpus: A Human-annotated Dialogue Dataset for Abstractive Summarization" 
      type: samsum
    metrics:
       - name: Validation ROGUE-1
         type: rogue-1
         value: 46.6619
       - name: Validation ROGUE-2
         type: rogue-2
         value: 23.3285
       - name: Validation ROGUE-L
         type: rogue-l
         value: 39.4811
       - name: Test ROGUE-1
         type: rogue-1
         value: 44.9932
       - name: Test ROGUE-2
         type: rogue-2
         value: 21.7286
       - name: Test ROGUE-L
         type: rogue-l
         value: 38.1921 
---
## `bart-base-samsum`
This model was obtained by fine-tuning `facebook/bart-base` on Samsum dataset.

## Usage
```python
from transformers import pipeline

summarizer = pipeline("summarization", model="lidiya/bart-base-samsum")
conversation = '''Jeff: Can I train a 🤗 Transformers model on Amazon SageMaker? 
Philipp: Sure you can use the new Hugging Face Deep Learning Container. 
Jeff: ok.
Jeff: and how can I get started? 
Jeff: where can I find documentation? 
Philipp: ok, ok you can find everything here. https://huggingface.co/blog/the-partnership-amazon-sagemaker-and-hugging-face                                           
'''
summarizer(conversation)
```

## Training procedure
- Colab notebook: https://colab.research.google.com/drive/1RInRjLLso9E2HG_xjA6j8JO3zXzSCBRF?usp=sharing

## Results
| key | value |
| --- | ----- |
| eval_rouge1 | 46.6619 |
| eval_rouge2 | 23.3285 |
| eval_rougeL | 39.4811 |
| eval_rougeLsum | 43.0482 |
| test_rouge1 | 44.9932 |
| test_rouge2 | 21.7286 |
| test_rougeL | 38.1921 |
| test_rougeLsum | 41.2672 |
