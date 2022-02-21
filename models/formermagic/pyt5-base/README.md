# Python T5 base model

Pre-trained model on CodeSearchNet Python dataset using a span-masking objective. The training objective and model were introduced in [this paper](https://arxiv.org/pdf/1910.10683.pdf) and first released in [this repository](https://github.com/google-research/text-to-text-transfer-transformer). PyT5 model used [git-t5](https://github.com/formermagic/git-t5) framework built on top of JAX/Flax to pre-train the model on a TPU v3-8 node.

# How to use

You can use this model to denoise span-masked sequences.

First, install the [git-t5](https://github.com/formermagic/git-t5) pip package:
```shell
> pip install git-t5
```

Next, download the model and tokenizer:
```python
from transformers import AutoModelForSeq2SeqLM, AutoTokenizer, 

model = AutoModelForSeq2SeqLM.from_pretrained("formermagic/pyt5-base")

tokenizer = AutoTokenizer.from_pretrained("formermagic/pyt5-base")
```

Finally, encode your input and generate the output sequence:
```python
from git_t5.utils import encode_input

text = """
def alias(self, annotationtype, set, fallback=False):
    if inspect.isclass(annotationtype): annotationtype = annotationtype.ANNOTATIONTYPE
    if annotationtype in self.set_alias and set in self.set_alias[annotationtype]:
        return self.set_alias[annotationtype][set]
    elif fallback:
        return set
    else:
        raise KeyError("No alias for set " + set)
"""

batch, max_length = encode_input(tokenizer, text, seed=22)
outputs = model.generate(batch["input_ids"], max_length=max_length, num_beams=1)
print(tokenizer.batch_decode(outputs[..., 1:]))
print(tokenizer.batch_decode(batch["labels"]))
```

You should see the following output:
```shell
['<extra_id_0>, fallback=<extra_id_1> inspect<extra_id_2>.set_alias<extra_id_3> return self.set<extra_id_4>) def fallback']
['<extra_id_0>, fallback=<extra_id_1> inspect<extra_id_2>.set_alias<extra_id_3> return self.set<extra_id_4>) </s></s>']
```

As you can see, the predicted result is very close to the target sequence. 