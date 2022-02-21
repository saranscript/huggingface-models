---
language: 
- es

tags:
- Emotion Analysis

---

**Note**: This model & model card are based on the [finetuned XLM-T for Sentiment Analysis](https://huggingface.co/cardiffnlp/twitter-xlm-roberta-base-sentiment)

# twitter-XLM-roBERTa-base for Emotion Analysis
This is a XLM-roBERTa-base model trained on ~198M tweets and finetuned for emotion analysis on Spanish language. This model was presented to EmoEvalEs competition, part of [IberLEF 2021 Conference](https://sites.google.com/view/iberlef2021/), where the proposed task was the classification of Spanish tweets between seven different classes: *anger*, *disgust*, *fear*, *joy*, *sadness*, *surprise*, and *other*. We achieved the first position in the competition with a macro-averaged F1 score of 71.70%. 
- [Our code for EmoEvalEs submission](https://github.com/gsi-upm/emoevales-iberlef2021).
- [EmoEvalEs Dataset](https://github.com/pendrag/EmoEvalEs)
## Example Pipeline with a [Tweet from @JaSantaolalla](https://twitter.com/JaSantaolalla/status/1398383243645177860)
```python
from transformers import pipeline
model_path = "daveni/twitter-xlm-roberta-emotion-es"
emotion_analysis = pipeline("text-classification", framework="pt", model=model_path, tokenizer=model_path)
emotion_analysis("Einstein dijo: Solo hay dos cosas infinitas, el universo y los pinches anuncios de bitcoin en Twitter. Paren ya carajo aaaaaaghhgggghhh me quiero murir")
```
```
[{'label': 'anger', 'score': 0.48307016491889954}]
```
## Full classification example
```python
from transformers import AutoModelForSequenceClassification
from transformers import AutoTokenizer, AutoConfig
import numpy as np
from scipy.special import softmax
# Preprocess text (username and link placeholders)
def preprocess(text):
    new_text = []
    for t in text.split(" "):
        t = '@user' if t.startswith('@') and len(t) > 1 else t
        t = 'http' if t.startswith('http') else t
        new_text.append(t)
    return " ".join(new_text)
model_path = "daveni/twitter-xlm-roberta-emotion-es"
tokenizer = AutoTokenizer.from_pretrained(model_path )
config = AutoConfig.from_pretrained(model_path )
# PT
model = AutoModelForSequenceClassification.from_pretrained(model_path )
text = "Se ha quedao bonito día para publicar vídeo, ¿no? Hoy del tema más diferente que hemos tocado en el canal."
text = preprocess(text)
print(text)
encoded_input = tokenizer(text, return_tensors='pt')
output = model(**encoded_input)
scores = output[0][0].detach().numpy()
scores = softmax(scores)
# Print labels and scores
ranking = np.argsort(scores)
ranking = ranking[::-1]
for i in range(scores.shape[0]):
    l = config.id2label[ranking[i]]
    s = scores[ranking[i]]
    print(f"{i+1}) {l} {np.round(float(s), 4)}")
```
Output: 

```
Se ha quedao bonito día para publicar vídeo, ¿no? Hoy del tema más diferente que hemos tocado en el canal.
1) joy 0.7887
2) others 0.1679
3) surprise 0.0152
4) sadness 0.0145
5) anger 0.0077
6) disgust 0.0033
7) fear 0.0027
```

#### Limitations and bias

- The dataset we used for finetuning was unbalanced, where almost half of the records belonged to the *other* class so there might be bias towards this class.


## Training data

Pretrained weights were left identical to the original model released by [cardiffnlp](https://huggingface.co/cardiffnlp/twitter-xlm-roberta-base). We used the [EmoEvalEs Dataset](https://github.com/pendrag/EmoEvalEs) for finetuning.

### BibTeX entry and citation info

```bibtex
Coming soon
```