---
pipeline_tag: sentence-similarity
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
widget:
- source_sentence: "hum baccho ko online classes ke liye free laptop dete hai"
- sentences: ["we provide free laptops to kids for online classes", "hum kids ko padhne ke liye free laptop dete h", "aaj bhut accha din hai"]

---

LaBSE model finetuned on English and Hindi-Latin (transliterated) similarity task.

LaBSE Research paper: https://ai.googleblog.com/2020/08/language-agnostic-bert-sentence.html

## Usage (Sentence-Transformers)
Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:
```
pip install -U sentence-transformers==1.2.0
```
Then you can use the model like this:

```python
from scipy.spatial.distance import cosine
def cos_sim(u,v):
    return 1 - cosine(u,v)
    
from sentence_transformers import SentenceTransformer
#  sentence-transformer version 1.2.0 is used

model = SentenceTransformer("salesken/similarity-eng-hin_latin")

#source sentence (hindi-latin)
sentence1 = 'hum baccho ko online classes ke liye free laptop dete hai'

#target sentence (english)
sentence2 = 'we provide free laptops to kids for online classes '

# it works both the ways (sentence1 sentence2 can be interchanged)

embedding_hin_latin  = model.encode(sentence1)
embedding_eng = model.encode(sentence2)

cos_sim(embedding_hin_latin,embedding_eng)
## 0.978


```

## Usage (HuggingFace Transformers)
Without [sentence-transformers](https://www.SBERT.net), you can use the model like this: First, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.

```python
from transformers import AutoTokenizer, AutoModel
import torch
# Load model from HuggingFace Hub
  
tokenizer = AutoTokenizer.from_pretrained("salesken/similarity-eng-hin_latin")

model = AutoModel.from_pretrained("salesken/similarity-eng-hin_latin")




```
