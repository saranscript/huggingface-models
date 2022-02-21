This repository doesn't contain a model, but only a tokenizer that can be used with the
`tokenizers` library.

This tokenizer is just a copy of `bert-base-uncased`.

```python
from tokenizers import Tokenizer
tokenizer = Tokenizer.from_pretrained("anthony/tokenizers-test")
```
