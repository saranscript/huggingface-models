SQuAD 1.1 question-answering based on T5-small. 
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

run_model("Who is the winner of 2009 olympics? \n Jack and Jill participated, but James won the games.")```
which should result in the following:
```
['James']
``` 

