# Twitter December 2021 (RoBERTa-base, 124M)

This is a RoBERTa-base model trained on 123.86M tweets until the end of December 2021.
More details and performance scores are available in the [TimeLMs paper](https://arxiv.org/abs/2202.03829).

Below, we provide some usage examples using the standard Transformers interface. For another interface more suited to comparing predictions and perplexity scores between models trained at different temporal intervals, check the [TimeLMs repository](https://github.com/cardiffnlp/timelms).

For other models trained until different periods, check this [table](https://github.com/cardiffnlp/timelms#released-models).

## Preprocess Text 
Replace usernames and links for placeholders: "@user" and "http".
If you're interested in retaining verified users which were also retained during training, you may keep the users listed [here](https://github.com/cardiffnlp/timelms/tree/main/data).
```python
def preprocess(text):
    new_text = []
    for t in text.split(" "):
        t = '@user' if t.startswith('@') and len(t) > 1 else t
        t = 'http' if t.startswith('http') else t
        new_text.append(t)
    return " ".join(new_text)
```

## Example Masked Language Model 

```python
from transformers import pipeline, AutoTokenizer

MODEL = "cardiffnlp/twitter-roberta-base-dec2021"
fill_mask = pipeline("fill-mask", model=MODEL, tokenizer=MODEL)
tokenizer = AutoTokenizer.from_pretrained(MODEL)

def print_candidates():
    for i in range(5):
        token = tokenizer.decode(candidates[i]['token'])
        score = candidates[i]['score']
        print("%d) %.5f %s" % (i+1, score, token))

texts = [
    "So glad I'm <mask> vaccinated.",
    "I keep forgetting to bring a <mask>.",
    "Looking forward to watching <mask> Game tonight!",
]
for text in texts:
    t = preprocess(text)
    print(f"{'-'*30}\n{t}")
    candidates = fill_mask(t)
    print_candidates()
```

Output: 

```
------------------------------
So glad I'm <mask> vaccinated.
1) 0.33211  fully
2) 0.26205  not
3) 0.22305  getting
4) 0.03790  still
5) 0.01817  all
------------------------------
I keep forgetting to bring a <mask>.
1) 0.04808  mask
2) 0.04628  book
3) 0.03597  lighter
4) 0.03391  pen
5) 0.02982  knife
------------------------------
Looking forward to watching <mask> Game tonight!
1) 0.34191  Squid
2) 0.23768  the
3) 0.15699  The
4) 0.02766  End
5) 0.01233  this
```

## Example Tweet Embeddings
```python
from transformers import AutoTokenizer, AutoModel, TFAutoModel
import numpy as np
from scipy.spatial.distance import cosine
from collections import Counter

def get_embedding(text):
  text = preprocess(text)
  encoded_input = tokenizer(text, return_tensors='pt')
  features = model(**encoded_input)
  features = features[0].detach().cpu().numpy() 
  features_mean = np.mean(features[0], axis=0) 
  return features_mean


MODEL = "cardiffnlp/twitter-roberta-base-dec2021"
tokenizer = AutoTokenizer.from_pretrained(MODEL)
model = AutoModel.from_pretrained(MODEL)

query = "The book was awesome"
tweets = ["I just ordered fried chicken 🐣", 
          "The movie was great",
          "What time is the next game?",
          "Just finished reading 'Embeddings in NLP'"]

sims = Counter()
for tweet in tweets:
    sim = 1 - cosine(get_embedding(query), get_embedding(tweet))
    sims[tweet] = sim

print('Most similar to: ', query)
print(f"{'-'*30}")
for idx, (tweet, sim) in enumerate(sims.most_common()):
    print("%d) %.5f %s" % (idx+1, sim, tweet))
```
Output: 

```
Most similar to:  The book was awesome
------------------------------
1) 0.99004 The movie was great
2) 0.96320 Just finished reading 'Embeddings in NLP'
3) 0.95858 I just ordered fried chicken 🐣
4) 0.95356 What time is the next game?
```

## Example Feature Extraction 

```python
from transformers import AutoTokenizer, AutoModel, TFAutoModel
import numpy as np

MODEL = "cardiffnlp/twitter-roberta-base-dec2021"
tokenizer = AutoTokenizer.from_pretrained(MODEL)

text = "Good night 😊"
text = preprocess(text)

# Pytorch
model = AutoModel.from_pretrained(MODEL)
encoded_input = tokenizer(text, return_tensors='pt')
features = model(**encoded_input)
features = features[0].detach().cpu().numpy() 
features_mean = np.mean(features[0], axis=0) 
#features_max = np.max(features[0], axis=0)

# # Tensorflow
# model = TFAutoModel.from_pretrained(MODEL)
# encoded_input = tokenizer(text, return_tensors='tf')
# features = model(encoded_input)
# features = features[0].numpy()
# features_mean = np.mean(features[0], axis=0) 
# #features_max = np.max(features[0], axis=0)
```