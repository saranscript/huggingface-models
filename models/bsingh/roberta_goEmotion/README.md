---
language: en
tags:
- text-classification
- pytorch
- roberta
- emotions
datasets:
- go_emotions
license: mit
widget:
- text: "I am not feeling well today."
---

## This model is trained for GoEmotions dataset which contains labeled 58k Reddit comments with 28 emotions
- admiration, amusement, anger, annoyance, approval, caring, confusion, curiosity, desire, disappointment, disapproval, disgust, embarrassment, excitement, fear, gratitude, grief, joy, love, nervousness, optimism, pride, realization, relief, remorse, sadness, surprise + neutral

## Training details:
- The training script is provided here: https://github.com/bsinghpratap/roberta_train_goEmotion
- Please feel free to start an issue in the repo if you have trouble running the model and I would try to respond as soon as possible.
- The model works well on most of the emotions except: 'desire', 'disgust', 'embarrassment', 'excitement', 'fear', 'grief', 'nervousness', 'pride', 'relief', 'remorse', 'surprise']
- I'll try to fine-tune the model further and update here if RoBERTa achieves a better performance.
- Each text datapoint can have more than 1 label. Most of the training set had 1 label: Counter({1: 36308, 2: 6541, 3: 532, 4: 28, 5: 1}). So currently I just used the first label for each of the datapoint. Not ideal but it does a decent job.

## Model Performance
============================================================<br>
Emotion: admiration<br>
============================================================<br>
GoEmotions Paper: 0.65<br>
RoBERTa: 0.62<br>
Support: 504<br>
============================================================<br>
Emotion: amusement<br>
============================================================<br>
GoEmotions Paper: 0.80<br>
RoBERTa: 0.78<br>
Support: 252<br>
============================================================<br>
Emotion: anger<br>
============================================================<br>
GoEmotions Paper: 0.47<br>
RoBERTa: 0.44<br>
Support: 197<br>
============================================================<br>
Emotion: annoyance<br>
============================================================<br>
GoEmotions Paper: 0.34<br>
RoBERTa: 0.22<br>
Support: 286<br>
============================================================<br>
Emotion: approval<br>
============================================================<br>
GoEmotions Paper: 0.36<br>
RoBERTa: 0.31<br>
Support: 318<br>
============================================================<br>
Emotion: caring<br>
============================================================<br>
GoEmotions Paper: 0.39<br>
RoBERTa: 0.24<br>
Support: 114<br>
============================================================<br>
Emotion: confusion<br>
============================================================<br>
GoEmotions Paper: 0.37<br>
RoBERTa: 0.29<br>
Support: 139<br>
============================================================<br>
Emotion: curiosity<br>
============================================================<br>
GoEmotions Paper: 0.54<br>
RoBERTa: 0.48<br>
Support: 233<br>
============================================================<br>
Emotion: disappointment<br>
============================================================<br>
GoEmotions Paper: 0.28<br>
RoBERTa: 0.18<br>
Support: 127<br>
============================================================<br>
Emotion: disapproval<br>
============================================================<br>
GoEmotions Paper: 0.39<br>
RoBERTa: 0.26<br>
Support: 220<br>
============================================================<br>
Emotion: gratitude<br>
============================================================<br>
GoEmotions Paper: 0.86<br>
RoBERTa: 0.84<br>
Support: 288<br>
============================================================<br>
Emotion: joy<br>
============================================================<br>
GoEmotions Paper: 0.51<br>
RoBERTa: 0.47<br>
Support: 116<br>
============================================================<br>
Emotion: love<br>
============================================================<br>
GoEmotions Paper: 0.78<br>
RoBERTa: 0.68<br>
Support: 169<br>
============================================================<br>
Emotion: neutral<br>
============================================================<br>
GoEmotions Paper: 0.68<br>
RoBERTa: 0.61<br>
Support: 1606<br>
============================================================<br>
Emotion: optimism<br>
============================================================<br>
GoEmotions Paper: 0.51<br>
RoBERTa: 0.52<br>
Support: 120<br>
============================================================<br>
Emotion: realization<br>
============================================================<br>
GoEmotions Paper: 0.21<br>
RoBERTa: 0.15<br>
Support: 109<br>
============================================================<br>
Emotion: sadness<br>
============================================================<br>
GoEmotions Paper: 0.49<br>
RoBERTa: 0.42<br>
Support: 108