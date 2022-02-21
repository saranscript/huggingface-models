---
language: id
tags:
  - indonesian-roberta-base-indolem-sentiment-classifier-fold-0
license: mit
datasets:
  - indolem
widget:
  - text: "Pelayanan hotel ini sangat baik."
---

## Indonesian RoBERTa Base IndoLEM Sentiment Classifier

Indonesian RoBERTa Base IndoLEM Sentiment Classifier is a sentiment-text-classification model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Indonesian RoBERTa Base](https://hf.co/flax-community/indonesian-roberta-base) model, which is then fine-tuned on [`indolem`](https://indolem.github.io/)'s [Sentiment Analysis](https://github.com/indolem/indolem/tree/main/sentiment) dataset consisting of Indonesian tweets and hotel reviews (Koto et al., 2020).

A 5-fold cross-validation experiment was performed, with splits provided by the original dataset authors. This model was trained on fold 0. You can find models trained on [fold 0](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-0), [fold 1](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-1), [fold 2](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-2), [fold 3](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-3), and [fold 4](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-4), in their respective links.

On **fold 0**, the model achieved an F1 of 86.42% on dev/validation and 83.12% on test. On all **5 folds**, the models achieved an average F1 of 84.14% on dev/validation and 84.64% on test.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                                                         | #params | Arch.        | Training/Validation data (text) |
| ------------------------------------------------------------- | ------- | ------------ | ------------------------------- |
| `indonesian-roberta-base-indolem-sentiment-classifier-fold-0` | 124M    | RoBERTa Base | `IndoLEM`'s Sentiment Analysis  |

## Evaluation Results

The model was trained for 10 epochs and the best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Accuracy | F1       | Precision | Recall   |
| ----- | ------------- | --------------- | -------- | -------- | --------- | -------- |
| 1     | 0.563500      | 0.420457        | 0.796992 | 0.626728 | 0.680000  | 0.581197 |
| 2     | 0.293600      | 0.281360        | 0.884712 | 0.811475 | 0.779528  | 0.846154 |
| 3     | 0.163000      | 0.267922        | 0.904762 | 0.844262 | 0.811024  | 0.880342 |
| 4     | 0.090200      | 0.335411        | 0.899749 | 0.838710 | 0.793893  | 0.888889 |
| 5     | 0.065200      | 0.462526        | 0.897243 | 0.835341 | 0.787879  | 0.888889 |
| 6     | 0.039200      | 0.423001        | 0.912281 | 0.859438 | 0.810606  | 0.914530 |
| 7     | 0.025300      | 0.452100        | 0.912281 | 0.859438 | 0.810606  | 0.914530 |
| 8     | 0.010400      | 0.525200        | 0.914787 | 0.855932 | 0.848739  | 0.863248 |
| 9     | 0.007100      | 0.513585        | 0.909774 | 0.850000 | 0.829268  | 0.871795 |
| 10    | 0.007200      | 0.537254        | 0.917293 | 0.864198 | 0.833333  | 0.897436 |

## How to Use

### As Text Classifier

```python
from transformers import pipeline

pretrained_name = "w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-0"

nlp = pipeline(
    "sentiment-analysis",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("Pelayanan hotel ini sangat baik.")
```

## Disclaimer

Do consider the biases which come from both the pre-trained RoBERTa model and `IndoLEM`'s Sentiment Analysis dataset that may be carried over into the results of this model.

## Author

Indonesian RoBERTa Base IndoLEM Sentiment Classifier was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.
