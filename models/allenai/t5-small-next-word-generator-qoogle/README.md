Next word generator trained on questions. Receives partial questions and tries to predict the next word.
Example use: 

```python
from transformers import T5Config, T5ForConditionalGeneration, T5Tokenizer

model_name = "allenai/t5-small-next-word-generator-qoogle"
tokenizer = T5Tokenizer.from_pretrained(model_name)
model = T5ForConditionalGeneration.from_pretrained(model_name)

def run_model(input_string, **generator_args):
    input_ids = tokenizer.encode(input_string, return_tensors="pt")
    res = model.generate(input_ids, **generator_args)
    output = tokenizer.batch_decode(res, skip_special_tokens=True)
    print(output)
    return output


run_model("Which")
run_model("Which two")
run_model("Which two counties")
run_model("Which two counties are")
run_model("Which two counties are the")
run_model("Which two counties are the biggest")
run_model("Which two counties are the biggest economic")
run_model("Which two counties are the biggest economic powers")

```
which should result in the following:
```
['one']
['statements']
['are']
['in']
['most']
['in']
['zones']
['of']
``` 

