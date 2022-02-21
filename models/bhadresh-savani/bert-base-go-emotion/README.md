---
language: 
- en
thumbnail: https://avatars3.githubusercontent.com/u/32437151?s=460&u=4ec59abc8d21d5feea3dab323d23a5860e6996a4&v=4
tags:
- text-classification
- go-emotion
- pytorch
license: apache-2.0
datasets:
- go_emotions
metrics:
- Accuracy
---
# Bert-Base-Uncased-Go-Emotion

## Model description:

## Training Parameters:
```
Num examples = 169208
Num Epochs = 3
Instantaneous batch size per device = 16
Total train batch size (w. parallel, distributed & accumulation) = 16
Gradient Accumulation steps = 1
Total optimization steps = 31728
```

## TrainOutput:
```
'train_loss': 0.12085497042373672, 
```

## Evalution Output:
```
 'eval_accuracy_thresh': 0.9614765048027039,
 'eval_loss': 0.1164659634232521
```

## Colab Notebook:
[Notebook](https://github.com/bhadreshpsavani/UnderstandingNLP/blob/master/go_emotion_of_transformers_multilabel_text_classification_v2.ipynb)