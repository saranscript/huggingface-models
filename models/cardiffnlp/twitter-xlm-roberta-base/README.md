---
language: multilingual
widget:
- text: "🤗🤗🤗<mask>"
- text: "🔥The goal of life is <mask> . 🔥"
- text: "Il segreto della vita è l’<mask> . ❤️"
- text: "Hasta <mask> 👋!"
---


# Twitter-XLM-Roberta-base
This is a XLM-Roberta-base model trained on ~198M multilingual tweets, described and evaluated in the [reference paper](https://arxiv.org/abs/2104.12250). To evaluate this and other LMs on Twitter-specific data, please refer to the [main repository](https://github.com/cardiffnlp/xlm-t). A usage example is provided below. 

## Computing tweet similarity

```python
def preprocess(text):
    new_text = []
    for t in text.split(" "):
        t = '@user' if t.startswith('@') and len(t) > 1 else t
        t = 'http' if t.startswith('http') else t
        new_text.append(t)
    return " ".join(new_text)

def get_embedding(text):
    text = preprocess(text)
    encoded_input = tokenizer(text, return_tensors='pt')
    features = model(**encoded_input)
    features = features[0].detach().numpy() 
    features_mean = np.mean(features[0], axis=0) 
    return features_mean

query = "Acabo de pedir pollo frito 🐣" #spanish

tweets = ["We had a great time! ⚽️", # english
          "We hebben een geweldige tijd gehad! ⛩", # dutch
          "Nous avons passé un bon moment! 🎥", # french
          "Ci siamo divertiti! 🍝"] # italian

d = defaultdict(int)
for tweet in tweets:
    sim = 1-cosine(get_embedding(query),get_embedding(tweet))
    d[tweet] = sim
    
print('Most similar to: ',query)
print('----------------------------------------')
for idx,x in enumerate(sorted(d.items(), key=lambda x:x[1], reverse=True)):
  print(idx+1,x[0])
```
```
Most similar to:  Acabo de pedir pollo frito 🐣
----------------------------------------
1 Ci siamo divertiti! 🍝
2 Nous avons passé un bon moment! 🎥
3 We had a great time! ⚽️
4 We hebben een geweldige tijd gehad! ⛩
```