---
datasets:
- wiki_split
widget:
- text: "Mary likes to play football in her freetime whenever she meets with her friends that are very nice people."    
---
# T5 model for sentence splitting in English
Sentence Split is the task of dividing a long sentence into multiple sentences. 
E.g.:
```
Mary likes to play football in her freetime whenever she meets with her friends that are very nice people.
```
could be split into
```
Mary likes to play football in her freetime whenever she meets with her friends.
```
```
Her friends are very nice people.
```
## How to use it in your code:
```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
tokenizer = AutoTokenizer.from_pretrained("flax-community/t5-large-wikisplit")
model = AutoModelForSeq2SeqLM.from_pretrained("flax-community/t5-large-wikisplit")
complex_sentence = "This comedy drama is produced by Tidy , the company she co-founded in 2008 with her husband David Peet , who is managing director ."
sample_tokenized = tokenizer(complex_sentence, return_tensors="pt")
answer = model.generate(sample_tokenized['input_ids'], attention_mask = sample_tokenized['attention_mask'], max_length=256, num_beams=5)
gene_sentence = tokenizer.decode(answer[0], skip_special_tokens=True)
gene_sentence
"""
Output:
This comedy drama is produced by Tidy. She co-founded Tidy in 2008 with her husband David Peet, who is managing director.
"""
```
## Datasets:
[Wiki_Split](https://research.google/tools/datasets/wiki-split/)
## Current Basline from [paper](https://arxiv.org/abs/1907.12461)
![baseline](./baseline.png)
## Our Results:
| Model | Exact | SARI | BLEU |
| --- | --- | --- | --- |
| [t5-base-wikisplit](https://huggingface.co/flax-community/t5-base-wikisplit) |  17.93 | 67.5438 | 76.9 |
| [t5-v1_1-base-wikisplit](https://huggingface.co/flax-community/t5-v1_1-base-wikisplit) | 18.1207 | 67.4873 | 76.9478 |
| [byt5-base-wikisplit](https://huggingface.co/flax-community/byt5-base-wikisplit) | 11.3582 | 67.2685 | 73.1682 |
| [t5-large-wikisplit](https://huggingface.co/flax-community/t5-large-wikisplit) | 18.6632 | 68.0501 | 77.1881 |