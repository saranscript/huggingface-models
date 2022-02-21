---
language: 
- da
license: apache-2.0
---
## daT5-base
A smaller version of [Google's mt5-base](https://huggingface.co/google/mt5-base) model, where the original model is reduced to only include Danish embeddings.

## How to use
```python
from transformers import AutoTokenizer, AutoModel
tokenizer = AutoTokenizer.from_pretrained("emillykkejensen/daT5-base")
model = AutoModel.from_pretrained("emillykkejensen/daT5-base")
```

## Further reading

[Gist](https://gist.github.com/emillykkejensen/8bf1b323495efc7252dee966e6bc1b5c) showing (in Danish) how the embeddings are extracted

[Article](https://towardsdatascience.com/how-to-adapt-a-multilingual-t5-model-for-a-single-language-b9f94f3d9c90) explaining how to do it by [David Dale](https://huggingface.co/cointegrated)

## Also check out
[daT5-large](https://huggingface.co/emillykkejensen/daT5-large)