---
pipeline_tag: sentence-similarity
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
---

# {mrp/simcse-model-distil-m-bert}

This is a [sentence-transformers](https://www.SBERT.net) by using m-Distil-BERT as the baseline model model: It maps sentences & paragraphs to a 768 dimensional dense vector space and can be used for tasks like clustering or semantic search.

<!--- Describe your model here -->
We use SimCSE [here](https://arxiv.org/pdf/2104.08821.pdf) and training the model with Thai Wikipedia [here](https://github.com/PyThaiNLP/ThaiWiki-clean/releases/tag/20210620?fbclid=IwAR1YcmZkb-xd1ibTWCJOcu98_FQ5x3ioZaGW1ME-VHy9fAQLhEr5tXTJygA)

## Usage (Sentence-Transformers)

Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer
sentences = ["ฉันนะคือคนรักชาติยังไงละ!", "พวกสามกีบล้มเจ้า!"]

model = SentenceTransformer('{MODEL_NAME}')
embeddings = model.encode(sentences)
print(embeddings)
```