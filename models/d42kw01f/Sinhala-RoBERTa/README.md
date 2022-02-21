# Description:

This is a smaller per-trained model on Sinhalese Language using Masked Language Modeling(MLM). And the model is trained on Oscar Sinhala dataset.

# How to Use:
The model can be used directly with a pipeline for masked language modeling:
```python
>>> from transformers import AutoTokenizer, AutoModelForMaskedLM, pipeline
>>> tokenizer = AutoTokenizer.from_pretrained("d42kw01f/Sinhala-RoBERTa")
>>> model = AutoModelForMaskedLM.from_pretrained("d42kw01f/Sinhala-RoBERTa")
>>> fill_mask = pipeline('fill-mask', model=model, tokenizer=tokenizer)
>>> fill_mask("මම ගෙදර <mask>.")
[{'score': 0.1822454035282135,
  'sequence': 'මම ගෙදර ආව.',
  'token': 701,
  'token_str': ' ආව'},
 {'score': 0.10513380169868469,
  'sequence': 'මම ගෙදර ය.',
  'token': 310,
  'token_str': ' ය'},
 {'score': 0.06417194753885269,
  'sequence': 'මම ගෙදර එක.',
  'token': 328,
  'token_str': ' එක'},
 {'score': 0.05026362091302872,
  'sequence': 'මම ගෙදර ඇත.',
  'token': 330,
  'token_str': ' ඇත'},
 {'score': 0.029960114508867264,
  'sequence': 'මම ගෙදර යනව.',
  'token': 834,
  'token_str': ' යනව'}]
  ```