---
pipeline_tag: sentence-similarity
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
---

## Usage

```
from sentence_transformers import SentenceTransformer, models
embedding_model = models.Transformer("yobi/klue-roberta-base-sts")
pooling_model = models.Pooling(
    embedding_model.get_word_embedding_dimension(),
    pooling_mode_mean_tokens=True,
)
model = SentenceTransformer(modules=[embedding_model,  pooling_model])
model.encode("안녕하세요.", convert_to_tensor=True)
```

