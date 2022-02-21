---
pipeline_tag: sentence-similarity
license: apache-2.0
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
---

# recobo/chemical-bert-uncased-simcse
```python
from sentence_transformers import SentenceTransformer

model_name = 'recobo/chemical-bert-uncased-simcse'

model = SentenceTransformer(model_name)
```