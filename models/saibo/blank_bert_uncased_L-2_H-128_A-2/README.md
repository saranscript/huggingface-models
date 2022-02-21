The weight of this model is randomly initiated and this can be particularly useful when we aim to train a language model from scratch or benchmark the effect of pretraining.

It's important to note that tokenizer of this random model is the same as the original pretrained model because it's not a trivial task to get a random tokenizer and it's less meaningful compared to the random weight.

A debatable advantage of pulling this model from Huggingface is to avoid using random seed in order to obtain the same randomness at each time.

The code to obtain such a random model:

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
# @Filename : random_model
# @Date : 2021-12-13-10-08

import os
from transformers import AutoModel, AutoTokenizer



def auto_name_blank_model(model_url:str):
    original_model_name:str = os.path.basename(model_url)
    return "blank_"+original_model_name

pretrained_model_url="google/bert_uncased_L-2_H-128_A-2"

tokenizer = AutoTokenizer.from_pretrained(pretrained_model_url)
model = AutoModel.from_pretrained(pretrained_model_url)
model.init_weights()
new_repo_name:str = auto_name_blank_model(pretrained_model_url)
model.push_to_hub(new_repo_name)
tokenizer.push_to_hub(new_repo_name)

# uploading files to an existing repo will overwrite the files without prompt.
```