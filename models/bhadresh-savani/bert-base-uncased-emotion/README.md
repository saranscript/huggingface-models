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
# bert-base-uncased-emotion

## Model description:

[Bert](https://arxiv.org/abs/1810.04805) is a Transformer Bidirectional Encoder based Architecture trained on MLM(Mask Language Modeling) objective

[bert-base-uncased](https://huggingface.co/bert-base-uncased) finetuned on the emotion dataset using HuggingFace Trainer with below training parameters
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
classifier = pipeline("text-classification",model='bhadresh-savani/bert-base-uncased-emotion', return_all_scores=True)
prediction = classifier("I love using transformers. The best part is wide range of support and its easy to use", )
print(prediction)

"""
output:
[[
{'label': 'sadness', 'score': 0.0005138228880241513}, 
{'label': 'joy', 'score': 0.9972520470619202}, 
{'label': 'love', 'score': 0.0007443308713845909}, 
{'label': 'anger', 'score': 0.0007404946954920888}, 
{'label': 'fear', 'score': 0.00032938539516180754}, 
{'label': 'surprise', 'score': 0.0004197491507511586}
]]
"""
```

## Dataset:
[Twitter-Sentiment-Analysis](https://huggingface.co/nlp/viewer/?dataset=emotion).

## Training procedure
[Colab Notebook](https://github.com/bhadreshpsavani/ExploringSentimentalAnalysis/blob/main/SentimentalAnalysisWithDistilbert.ipynb)
follow the above notebook by changing the model name from distilbert to bert

## Eval results
```json
{
 'test_accuracy': 0.9405,
 'test_f1': 0.9405920712282673,
 'test_loss': 0.15769127011299133,
 'test_runtime': 10.5179,
 'test_samples_per_second': 190.152,
 'test_steps_per_second': 3.042
 }
```

## Reference:
* [Natural Language Processing with Transformer By Lewis Tunstall, Leandro von Werra, Thomas Wolf](https://learning.oreilly.com/library/view/natural-language-processing/9781098103231/)