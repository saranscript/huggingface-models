This is a gpt-2 model trained on 4000 rows of this [dataset](https://huggingface.co/datasets/bs-modeling-metadata/OSCAR_Entity_13_000).

Code to generate text using this model:
```
from transformers import AutoModelWithLMHead, AutoTokenizer

text = "The students pursuing their masters at Harvard [["   #Special token used for entities is [[ ]]

tokenizer = AutoTokenizer.from_pretrained("gpt2")
model = AutoModelWithLMHead.from_pretrained("manandey/gpt2-entity")
inputs = tokenizer(text, return_tensors="pt")

sample_outputs = model.generate(
                                **inputs,
                                do_sample=True,   
                                min_length=100, 
                                max_length=300,
                                top_k=30,                                 
                                top_p=0.7,        
                                temperature=0.9,
                                repetition_penalty=2.0,
                                num_return_sequences=5
                                )

for i, sample_output in enumerate(sample_outputs):
  print("{}: {}\n\n".format(i, tokenizer.decode(sample_output, skip_special_tokens=True)))
```