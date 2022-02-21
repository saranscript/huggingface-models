---
language: en
thumbnail: https://salesken.ai/assets/images/logo.png
license: apache-2.0
inference: false
widget:
 - text: "every moment is a fresh beginning"
 
tags: salesken
---

Use this model to generate variations to augment the training data used for NLU systems. 
```python
from transformers import AutoTokenizer, AutoModelWithLMHead 

import torch
if torch.cuda.is_available():
    device = torch.device("cuda")
else :
    device = "cpu"

tokenizer = AutoTokenizer.from_pretrained("salesken/paraphrase_generation")  
model = AutoModelWithLMHead.from_pretrained("salesken/paraphrase_generation").to(device)

input_query="every moment is a fresh beginning"
query= input_query + " ~~ "

input_ids = tokenizer.encode(query.lower(), return_tensors='pt').to(device)
sample_outputs = model.generate(input_ids,
                                do_sample=True,
                                num_beams=1, 
                                max_length=128,
                                temperature=0.9,
                                top_p= 0.99,
                                top_k = 30,
                                num_return_sequences=40)
paraphrases = []
for i in range(len(sample_outputs)):
    r = tokenizer.decode(sample_outputs[i], skip_special_tokens=True).split('||')[0]
    r = r.split(' ~~ ')[1]
    if r not in paraphrases:
        paraphrases.append(r)

print(paraphrases)


```


To evaluate if a paraphrase is a semantic variation to the input query or just a surface level variation & rank the generated paraphrases, use the following model:

https://huggingface.co/salesken/paraphrase_diversity_ranker


