# random-roberta-mini

We introduce random-roberta-mini, which is a unpretrained version of a mini RoBERTa model(4 layer and 256 heads). The weight of random-roberta-mini is randomly initiated and this can be particularly useful when we aim to train a language model from scratch or benchmark the effect of pretraining.

It's important to note that tokenizer of random-roberta-mini is the same as roberta-base because it's not a trivial task to get a random tokenizer and it's less meaningful compared to the random weight.

A debatable advantage of pulling random-roberta-mini from Huggingface is to avoid using random seed in order to obtain the same randomness at each time.

The code to obtain such random model:

```python

from transformers import RobertaConfig, RobertaModel

    
def get_custom_blank_roberta(h=768, l=12):

    # Initializing a RoBERTa configuration
    configuration = RobertaConfig(num_attention_heads=h, num_hidden_layers=l)

    # Initializing a model from the configuration
    model = RobertaModel(configuration)

    return model

rank="mini"
h=256
l=4
model_type = "roberta"
tokenizer = AutoTokenizer.from_pretrained("roberta-base")
model_name ="random-"+model_type+"-"+rank
model = get_custom_blank_roberta(h, l)
```
