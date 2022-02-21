---
tags:
- flair
- token-classification
- sequence-tagger-model
language: fr
widget:
- text: "12 séries de 2 minutes 38 minutes entre série"

---
#### This model is used in the [Speech Interval Timer app](https://medium.com/@amtam0/speech-interval-timer-app-using-transformers-1df8fa3821d5)

7-class NER French model using [Flair TransformerWordEmbeddings - camembert-base](https://github.com/flairNLP/flair/).

| **tag**                        | **meaning** |
|---------------------------------|-----------|
| nb_rounds         | Number of rounds | 
| duration_br_sd         | Duration btwn rounds in seconds | 
| duration_br_min         | Duration btwn rounds in minutes | 
| duration_br_hr         | Duration btwn rounds in hours | 
| duration_wt_sd         | workout duration in seconds | 
| duration_wt_min         | workout duration in minutes | 
| duration_wt_hr         | workout duration in hours | 
---
The dataset was created manually (perfectible). Sentences example : 
```
19 séries de 3 minutes 21 minutes entre chaque série
préparer 7 sets de 32 secondes
lance 13 séries de 26 secondes
initie 8 series de 3 minutes
2 séries de 30 secondes 35 minutes entre chaque série
...
```