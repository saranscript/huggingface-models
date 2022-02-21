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
# Albert-base-v2-emotion

## Model description:
[Albert](https://arxiv.org/pdf/1909.11942v6.pdf) is A Lite BERT architecture that has significantly fewer parameters than a traditional BERT architecture.

[Albert-base-v2](https://huggingface.co/albert-base-v2) finetuned on the emotion dataset using HuggingFace Trainer with below Hyperparameters
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
classifier = pipeline("text-classification",model='bhadresh-savani/albert-base-v2-emotion', return_all_scores=True)
prediction = classifier("I love using transformers. The best part is wide range of support and its easy to use", )
print(prediction)

"""
Output:
[[
{'label': 'sadness', 'score': 0.010403595864772797}, 
{'label': 'joy', 'score': 0.8902180790901184}, 
{'label': 'love', 'score': 0.042532723397016525}, 
{'label': 'anger', 'score': 0.041297927498817444}, 
{'label': 'fear', 'score': 0.011772023513913155}, 
{'label': 'surprise', 'score': 0.0037756056990474463}
]]
"""
```

## Dataset:
[Twitter-Sentiment-Analysis](https://huggingface.co/nlp/viewer/?dataset=emotion).

## Training procedure
[Colab Notebook](https://github.com/bhadreshpsavani/ExploringSentimentalAnalysis/blob/main/SentimentalAnalysisWithDistilbert.ipynb)

## Eval results
```json
{
'test_accuracy': 0.936,
 'test_f1': 0.9365658988006296,
 'test_loss': 0.15278364717960358,
 'test_runtime': 10.9413,
 'test_samples_per_second': 182.794,
 'test_steps_per_second': 2.925
 }
```

## Reference:
* [Natural Language Processing with Transformer By Lewis Tunstall, Leandro von Werra, Thomas Wolf](https://learning.oreilly.com/library/view/natural-language-processing/9781098103231/)