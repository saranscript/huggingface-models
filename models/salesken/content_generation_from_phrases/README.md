
---
tags: salesken
license: apache-2.0
inference: false

---

We attempted an entailment-encouraging text generation model to generate content , given a short phrase . 

Some the generated sentences like below, for the phrase "data science beginner", really got us excited about the potential applications:

<b> ['Where can I find a list of questions, tutorials, and resources for getting a data scientist job?
'Do you know of any research articles about how to improve your skills as a Data Science/Data Management Programmer? ',
'What are the pros and cons to having a Data Science/Data Mining Masters? '] .</b>



Utility of the model ? Automate your conversational AI training data creation process by feeding some meaningful phrases to the model , to generate entailment-encouraging sentences; select the most diverse sentences and generate semantic variations for these, using our paraphrase generation model (https://huggingface.co/salesken/paraphrase_generation), and rank the generated sentence encouraging diversity by using our NLG ranker model (https://huggingface.co/salesken/paraphrase_diversity_ranker)


```python
from transformers import AutoTokenizer, AutoModelWithLMHead  
import pprint
import torch
if torch.cuda.is_available():
    device = torch.device("cuda")
else:
    device = "cpu"
    
    
tokenizer = AutoTokenizer.from_pretrained("salesken/content_generation_from_phrases") 
model = AutoModelWithLMHead.from_pretrained("salesken/content_generation_from_phrases").to(device)


input_query=["data science beginner"]
query = "<|startoftext|> " + input_query[0] + " ~~"

input_ids = tokenizer.encode(query.lower(), return_tensors='pt').to(device)
sample_outputs = model.generate(input_ids,
                                do_sample=True,
                                num_beams=1, 
                                max_length=256,
                                temperature=0.9,
                                top_k = 30,
                                num_return_sequences=100)
content = []
for i in range(len(sample_outputs)):
    r = tokenizer.decode(sample_outputs[i], skip_special_tokens=True).split('||')[0]
    r = r.split(' ~~ ')[1]
    if r not in content:
        content.append(r)

pprint.pprint(content)
```

You may use our ranker model to rank the generated content to encourage diversity.

https://huggingface.co/salesken/paraphrase_diversity_ranker


```
from transformers import AutoTokenizer, AutoModelForSequenceClassification  
import torch
import pandas as pd
import numpy as np
rank_tokenizer = AutoTokenizer.from_pretrained("salesken/paraphrase_diversity_ranker")
rank_model = AutoModelForSequenceClassification.from_pretrained("salesken/paraphrase_diversity_ranker")

content_pairs=list(pd.MultiIndex.from_product([input_query, content]))

features = rank_tokenizer(content_pairs,  padding=True, truncation=True, return_tensors="pt")
rank_model.eval()
with torch.no_grad():
    scores = rank_model(**features).logits
    label_mapping = ['surface_level_variation', 'semantic_variation']
    labels = [label_mapping[score_max] for score_max in scores.argmax(dim=1)]

generated_content= np.array(content)[scores[:,1].sort(descending=True).indices].tolist()


```

