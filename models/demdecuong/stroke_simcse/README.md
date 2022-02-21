This is finetune version of [SimCSE: Simple Contrastive Learning of Sentence Embeddings](https://arxiv.org/abs/2104.08821)
, train unsupervised on 570K stroke sentences from : stroke books, quora medical, quora's stroke and human annotates.

### Extract sentence representation
```
from transformers import AutoTokenizer, AutoModel  
tokenizer = AutoTokenizer.from_pretrained("demdecuong/stroke_simcse")
model = AutoModel.from_pretrained("demdecuong/stroke_simcse")

text = "What are disease related to red stroke's causes?"
inputs = tokenizer(text, return_tensors='pt')
outputs = model(**inputs)[1]
```
### Build up embedding for database

```
database = [
    'What is the daily checklist for stroke returning home',
    'What are some tips for stroke adapt new life',
    'What  should I consider when using nursing-home care'
]

embedding = torch.zeros((len(database),768))

for i in range(len(database)):
  inputs = tokenizer(database[i], return_tensors="pt")
  outputs = model(**inputs)[1]
  embedding[i] = outputs

print(embedding.shape)
```

### Result
On our Poc testset , which contains pairs of matching question related to stroke from human-generated. 

| Model  | Top-1 Accuracy |
| ------------- | ------------- |
| SimCSE (supervised)  | 75.83  |
| SimCSE (ours)  | 76.66  |