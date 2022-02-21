```python
import tempfile

from tokenizers import Tokenizer, models
from transformers import PreTrainedTokenizerFast

model_max_length = 4
vocab = [(chr(i), i) for i in range(256)]
tokenizer = Tokenizer(models.Unigram(vocab))
with tempfile.NamedTemporaryFile() as f:
    tokenizer.save(f.name)
    real_tokenizer = PreTrainedTokenizerFast(tokenizer_file=f.name, model_max_length=model_max_length)

real_tokenizer._tokenizer.save("dummy/tokenizer.json")

```

config uses Albert which works with a minimal `config.json`