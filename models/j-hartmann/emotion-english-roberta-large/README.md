---

language: "en"
tags:
- roberta
- sentiment
- emotion
- twitter
- reddit

widget:
- text: "Oh wow. I didn't know that."
- text: "This movie always makes me cry.."
- text: "Oh Happy Day"

---

## Description ℹ

With this model, you can classify emotions in English text data. The model was trained on 6 diverse datasets and predicts Ekman's 6 basic emotions, plus a neutral class:

1) anger 🤬
2) disgust 🤢
3) fear 😨
4) joy 😀
5) neutral 😐
6) sadness 😭
7) surprise 😲

The model is a fine-tuned checkpoint of [RoBERTa-large](https://huggingface.co/roberta-large). 

For further details on this emotion model, please refer to the model card of its [DistilRoBERTa](https://huggingface.co/j-hartmann/emotion-english-distilroberta-base) version.