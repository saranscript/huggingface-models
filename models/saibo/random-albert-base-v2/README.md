# random-albert-base-v2

We introduce random-albert-base-v2, which is a unpretrained version of Albert model. The weight of random-albert-base-v2 is randomly initiated and this can be particularly useful when we aim to train a language model from scratch or benchmark the effect of pretraining.

It's important to note that tokenizer of random-albert-base-v2 is the same as albert-base-v2 because it's not a trivial task to get a random tokenizer and it's less meaningful compared to the random weight.

A debatable advantage of pulling random-albert-base-v2 from Huggingface is to avoid using random seed in order to obtain the same randomness at each time.

The code to obtain a such random model:

```python

from transformers import AutoTokenizer, AutoModelForSequenceClassification

def get_blank_model_from_hf(model_name="bert-base-cased"):
    model = AutoModelForSequenceClassification.from_pretrained(model_name, num_labels=5)
    tokenizer = AutoTokenizer.from_pretrained(model_name)
    model.base_model.init_weights()
    model_name = "random-" + model_name
    base_model= model.base_model
    return base_model, tokenizer, model_name
```
