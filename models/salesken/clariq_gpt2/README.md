
---
tags: 
- salesken
- gpt2
- lm-head
- causal-lm
- salesken
license: apache-2.0
inference: False

---


The ClariQ challenge [3] is organized as part of the Search-oriented Conversational AI (SCAI) EMNLP workshop in 2020. The main aim of the conversational systems is to return an appropriate answer in response to the user requests. However, some user requests might be ambiguous. In Information Retrieval (IR) settings such a situation is handled mainly through the diversification of search result page. It is however much more challenging in dialogue settings. Hence, we aim to study the following situation for dialogue settings:<br />

A user is asking an ambiguous question (where ambiguous question is a question to which one can return > 1 possible answers);, instead of trying to answer it directly, ask a good clarifying question.


 __Query: Serve your models directly from Hugging Face infrastructure and run large scale NLP models in milliseconds with just a few lines of code__

***Top 5 clarifications generated:*** <br />
 - are you looking for a suitable cloud platform to run your models on  (Score: 0.3862) <br />
 - are you looking for a quick test or a more complex model  (Score: 0.3364) <br />
 - how would you like your nlp model to be used  (Score: 0.3249) <br />
 - are you looking for a suitable ldl to use as a server or a client  (Score: 0.3182) <br />
 - how would you like to consume the nlp model  (Score: 0.2842) <br />
 
 
```python
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("salesken/clariq_gpt2")
model = AutoModelWithLMHead.from_pretrained("salesken/clariq_gpt2") 

input_query="Serve your models directly from Hugging Face infrastructure and run large scale NLP models in milliseconds with just a few lines of code"

query= input_query + " ~~ "

input_ids = tokenizer.encode(query.lower(), return_tensors='pt')
sample_outputs = model.generate(input_ids,
                                do_sample=True,
                                num_beams=1, 
                                max_length=128,
                                temperature=0.9,
                                top_k = 40,
                                num_return_sequences=10)
clarifications_gen = []
for i in range(len(sample_outputs)):
    r = tokenizer.decode(sample_outputs[i], skip_special_tokens=True).split('||')[0]
    r = r.split(' ~~ ~~')[1]
    if r not in clarifications_gen:
        clarifications_gen.append(r)

print(clarifications_gen)

# to select the top n results:

from sentence_transformers import SentenceTransformer, util
import torch
embedder = SentenceTransformer('paraphrase-distilroberta-base-v1')

corpus = clarifications_gen
corpus_embeddings = embedder.encode(corpus, convert_to_tensor=True)

query = input_query.lower()
query_embedding = embedder.encode(query, convert_to_tensor=True)
cos_scores = util.pytorch_cos_sim(query_embedding, corpus_embeddings)[0]
top_results = torch.topk(cos_scores, k=5)
print("Top clarifications generated :")
for score, idx in zip(top_results[0], top_results[1]):
    print(corpus[idx], "(Score: {:.4f})".format(score))

```