---
language: 
- en
thumbnail: https://avatars3.githubusercontent.com/u/32437151?s=460&u=4ec59abc8d21d5feea3dab323d23a5860e6996a4&v=4
tags:
- text-classification
- emotion
- pytorch
license: apache-2.0
datasets:
- emotion
metrics:
- Accuracy, F1 Score
---
# robert-base-emotion

## Model description:
[roberta](https://arxiv.org/abs/1907.11692) is Bert with better hyperparameter choices so they said it's Robustly optimized Bert during pretraining.

[roberta-base](https://huggingface.co/roberta-base) finetuned on the emotion dataset using HuggingFace Trainer with below Hyperparameters
```
 learning rate 2e-5, 
 batch size 64,
 num_train_epochs=8,
```

## Model Performance Comparision on Emotion Dataset from Twitter:

| Model | Accuracy | F1 Score |  Test Sample per Second |
| --- | --- | --- | --- |
| [Distilbert-base-uncased-emotion](https://huggingface.co/bhadresh-savani/distilbert-base-uncased-emotion) | 93.8 | 93.79 | 398.69 |
| [Bert-base-uncased-emotion](https://huggingface.co/bhadresh-savani/bert-base-uncased-emotion) | 94.05 | 94.06 | 190.152 |
| [Roberta-base-emotion](https://huggingface.co/bhadresh-savani/roberta-base-emotion) | 93.95 | 93.97| 195.639 |
| [Albert-base-v2-emotion](https://huggingface.co/bhadresh-savani/albert-base-v2-emotion) | 93.6 | 93.65 | 182.794 |

## How to Use the model:
```python
from transformers import pipeline
classifier = pipeline("text-classification",model='bhadresh-savani/roberta-base-emotion', return_all_scores=True)
prediction = classifier("I love using transformers. The best part is wide range of support and its easy to use", )
print(prediction)

"""
Output:
[[
{'label': 'sadness', 'score': 0.002281982684507966}, 
{'label': 'joy', 'score': 0.9726489186286926}, 
{'label': 'love', 'score': 0.021365027874708176}, 
{'label': 'anger', 'score': 0.0026395076420158148}, 
{'label': 'fear', 'score': 0.0007162453257478774}, 
{'label': 'surprise', 'score': 0.0003483477921690792}
]]
"""
```

## Dataset:
[Twitter-Sentiment-Analysis](https://huggingface.co/nlp/viewer/?dataset=emotion).

## Training procedure
[Colab Notebook](https://github.com/bhadreshpsavani/ExploringSentimentalAnalysis/blob/main/SentimentalAnalysisWithDistilbert.ipynb)
follow the above notebook by changing the model name to roberta

## Eval results
```json
{
 'test_accuracy': 0.9395,
 'test_f1': 0.9397328860104454,
 'test_loss': 0.14367154240608215,
 'test_runtime': 10.2229,
 'test_samples_per_second': 195.639,
 'test_steps_per_second': 3.13
 }
```

## Reference:
* [Natural Language Processing with Transformer By Lewis Tunstall, Leandro von Werra, Thomas Wolf](https://learning.oreilly.com/library/view/natural-language-processing/9781098103231/)