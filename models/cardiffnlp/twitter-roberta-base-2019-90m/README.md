# Twitter 2021 90M (RoBERTa-base)

This is a RoBERTa-base model trained on 90M tweets until the end of 2019.
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

MODEL = "cardiffnlp/twitter-roberta-base-2019-90m"
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
1) 0.28870  getting
2) 0.28611  not
3) 0.15485  fully
4) 0.07357  self
5) 0.01812  being
------------------------------
I keep forgetting to bring a <mask>.
1) 0.12194  book
2) 0.04396  pillow
3) 0.04202  bag
4) 0.03038  wallet
5) 0.02729  charger
------------------------------
Looking forward to watching <mask> Game tonight!
1) 0.65505  End
2) 0.19230  The
3) 0.03856  the
4) 0.01223  end
5) 0.00978  this
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


MODEL = "cardiffnlp/twitter-roberta-base-2019-90m"
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
1) 0.99078 The movie was great
2) 0.96701 Just finished reading 'Embeddings in NLP'
3) 0.96037 I just ordered fried chicken 🐣
4) 0.95919 What time is the next game?
```

## Example Feature Extraction 

```python
from transformers import AutoTokenizer, AutoModel, TFAutoModel
import numpy as np

MODEL = "cardiffnlp/twitter-roberta-base-2019-90m"
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