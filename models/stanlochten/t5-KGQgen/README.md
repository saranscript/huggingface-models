T5-base model fine-tuned for question generation from knowledge graphs. Can be used to generate questions from linearized knowledge graphs, meaning graphs in the form of its all its triples listed in the following format:

`<A> answer node(s) <H> head <R> relation <T> tail <H> head <R> relation <T> tail ... etc ...`,
where `answer node(s)` refers to the node(s) which should contain the answer to the generated question.


To load the model:

```
from transformers import T5ForConditionalGeneration, T5TokenizerFast
model = T5ForConditionalGeneration.from_pretrained('stanlochten/t5-KGQgen')
tokenizer = T5TokenizerFast.from_pretrained('t5-base',  extra_ids=0, 
            additional_special_tokens = ['<A>', '<H>', '<R>', '<T>'])
```

To generate questions from your graphs, where `graphs` is a list of strings for each graph:
```
print('Tokenizing...')
inputs = tokenizer(graphs, return_tensors="pt", padding=True, truncation=True)
print('Predicting...')
y_hats = model.generate(inputs.input_ids)
print('Decoding...')
preds = tokenizer.batch_decode(y_hats, skip_special_tokens=True, clean_up_tokenization_spaces=True)
```

Good luck!