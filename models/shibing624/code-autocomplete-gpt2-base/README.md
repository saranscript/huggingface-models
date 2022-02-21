---
language: 
- en
tags:
- code
- autocomplete
- pytorch
- en
license: "apache-2.0"
---

# GPT2 for Code AutoComplete Model
code-autocomplete, a code completion plugin for Python.

**code-autocomplete** can automatically complete the code of lines and blocks with GPT2.

## Usage

Open source repo：[code-autocomplete](https://github.com/shibing624/code-autocomplete)，support GPT2 model, usage：

```python
from autocomplete.gpt2_coder import GPT2Coder

m = GPT2Coder("shibing624/code-autocomplete-gpt2-base")
print(m.generate('import torch.nn as')[0])
```

Also, use huggingface/transformers：

*Please use 'GPT2' related functions to load this model!*

```python
import os
import torch
from transformers import GPT2Tokenizer, GPT2LMHeadModel

os.environ["KMP_DUPLICATE_LIB_OK"] = "TRUE"
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

tokenizer = GPT2Tokenizer.from_pretrained("shibing624/code-autocomplete-gpt2-base")
model = GPT2LMHeadModel.from_pretrained("shibing624/code-autocomplete-gpt2-base")
model.to(device)
prompts = [
    """from torch import nn
    class LSTM(Module):
        def __init__(self, *,
                     n_tokens: int,
                     embedding_size: int,
                     hidden_size: int,
                     n_layers: int):""",
    """import numpy as np
    import torch
    import torch.nn as""",
    "import java.util.ArrayList",
    "def factorial(n):",
]
for prompt in prompts:
    input_ids = tokenizer.encode(prompt, add_special_tokens=False, return_tensors='pt').to(device)
    outputs = model.generate(input_ids=input_ids,
                             max_length=64 + len(prompt),
                             temperature=1.0,
                             top_k=50,
                             top_p=0.95,
                             repetition_penalty=1.0,
                             do_sample=True,
                             num_return_sequences=1,
                             length_penalty=2.0,
                             early_stopping=True)
    decoded = tokenizer.decode(outputs[0], skip_special_tokens=True)
    print(decoded)
    print("=" * 20)
```

output:
```shell
from torch import nn
    class LSTM(Module):
        def __init__(self, *,
                     n_tokens: int,
                     embedding_size: int,
                     hidden_size: int,
                     n_layers: int):
            self.embedding_size = embedding_size
====================
import numpy as np
import torch
import torch.nn as nn
import torch.nn.functional as F
```

Model files：
```
code-autocomplete-gpt2-base
├── config.json
├── merges.txt
├── pytorch_model.bin
├── special_tokens_map.json
├── tokenizer_config.json
└── vocab.json
```

### Train data
#### pytorch_awesome projects source code

download [code-autocomplete](https://github.com/shibing624/code-autocomplete),
```shell
cd autocomplete
python create_dataset.py
```

If you want train code-autocomplete GPT2 model，refer [https://github.com/shibing624/code-autocomplete/blob/main/autocomplete/gpt2_coder.py](https://github.com/shibing624/code-autocomplete/blob/main/autocomplete/gpt2_coder.py)


### About GPT2

Test the whole generation capabilities here: https://transformer.huggingface.co/doc/gpt2-large

Pretrained model on English language using a causal language modeling (CLM) objective. It was introduced in
[this paper](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)
and first released at [this page](https://openai.com/blog/better-language-models/).

Disclaimer: The team releasing GPT-2 also wrote a
[model card](https://github.com/openai/gpt-2/blob/master/model_card.md) for their model. Content from this model card
has been written by the Hugging Face team to complete the information they provided and give specific examples of bias.


## Citation

```latex
@misc{code-autocomplete,
  author = {Xu Ming},
  title = {code-autocomplete: Code AutoComplete with GPT model},
  year = {2022},
  publisher = {GitHub},
  journal = {GitHub repository},
  url = {https://github.com/shibing624/code-autocomplete},
}
```
