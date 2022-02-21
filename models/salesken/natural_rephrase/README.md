---

license: apache-2.0
inference: false
widget:
 - text: "Hey Siri, Send message to mom to say thank you for the delicious dinner yesterday"

---

NLG model trained on the rephrase generation dataset published by Fb 

Paper : https://research.fb.com/wp-content/uploads/2020/12/Sound-Natural-Content-Rephrasing-in-Dialog-Systems.pdf

Paper Abstract :
" We introduce a new task of rephrasing for a more natural virtual assistant. Currently, vir- tual assistants work in the paradigm of intent- slot tagging and the slot values are directly passed as-is to the execution engine. However, this setup fails in some scenarios such as mes- saging when the query given by the user needs to be changed before repeating it or sending it to another user. For example, for queries like ‘ask my wife if she can pick up the kids’ or ‘re- mind me to take my pills’, we need to rephrase the content to ‘can you pick up the kids’and
‘take your pills’. In this paper, we study the problem of rephrasing with messaging as a use case and release a dataset of 3000 pairs of original query and rephrased query.. " 

Training data :
http://dl.fbaipublicfiles.com/rephrasing/rephrasing_dataset.tar.gz

```python
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("salesken/natural_rephrase")
model = AutoModelWithLMHead.from_pretrained("salesken/natural_rephrase")


Input_query="Hey Siri, Send message to mom to say thank you for the delicious dinner yesterday"
query= Input_query + " ~~ "
input_ids = tokenizer.encode(query.lower(), return_tensors='pt')
sample_outputs = model.generate(input_ids,
                            do_sample=True,
                            num_beams=1, 
                            max_length=len(Input_query),
                            temperature=0.2,
                            top_k = 10,
                            num_return_sequences=1)
for i in range(len(sample_outputs)):
    result = tokenizer.decode(sample_outputs[i], skip_special_tokens=True).split('||')[0].split('~~')[1]
    print(result)

```

