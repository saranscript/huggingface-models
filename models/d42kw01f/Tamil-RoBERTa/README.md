# Description:

This is a smaller per-trained model on Tamil Language using Masked Language Modeling(MLM). And the model is trained on Oscar Tamil dataset.

# How to Use:
The model can be used directly with a pipeline for masked language modeling:
```python
>>> from transformers import AutoTokenizer, AutoModelForMaskedLM, pipeline
>>> tokenizer = AutoTokenizer.from_pretrained("d42kw01f/Tamil-RoBERTa")
>>> model = AutoModelForMaskedLM.from_pretrained("d42kw01f/Tamil-RoBERTa")
>>> fill_mask = pipeline('fill-mask', model=model, tokenizer=tokenizer)
>>> fill_mask("நான் வீட்டு <mask>.")
```