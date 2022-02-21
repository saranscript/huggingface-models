---
language: id
tags:
  - indonesian-roberta-base-indolem-sentiment-classifier-fold-2
license: mit
datasets:
  - indolem
widget:
  - text: "Pelayanan hotel ini sangat baik."
---

## Indonesian RoBERTa Base IndoLEM Sentiment Classifier

Indonesian RoBERTa Base IndoLEM Sentiment Classifier is a sentiment-text-classification model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Indonesian RoBERTa Base](https://hf.co/flax-community/indonesian-roberta-base) model, which is then fine-tuned on [`indolem`](https://indolem.github.io/)'s [Sentiment Analysis](https://github.com/indolem/indolem/tree/main/sentiment) dataset consisting of Indonesian tweets and hotel reviews (Koto et al., 2020).

A 5-fold cross-validation experiment was performed, with splits provided by the original dataset authors. This model was trained on fold 0. You can find models trained on [fold 0](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-0), [fold 1](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-1), [fold 2](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-2), [fold 3](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-3), and [fold 4](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-4), in their respective links.

On **fold 2**, the model achieved an F1 of 83.05% on dev/validation and 82.89% on test. On all **5 folds**, the models achieved an average F1 of 84.14% on dev/validation and 84.64% on test.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                                                         | #params | Arch.        | Training/Validation data (text) |
| ------------------------------------------------------------- | ------- | ------------ | ------------------------------- |
| `indonesian-roberta-base-indolem-sentiment-classifier-fold-2` | 124M    | RoBERTa Base | `IndoLEM`'s Sentiment Analysis  |

## Evaluation Results

The model was trained for 10 epochs and the best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Accuracy | F1       | Precision | Recall   |
| ----- | ------------- | --------------- | -------- | -------- | --------- | -------- |
| 1     | 0.563300      | 0.436885        | 0.786967 | 0.568528 | 0.700000  | 0.478632 |
| 2     | 0.307800      | 0.301497        | 0.864662 | 0.763158 | 0.783784  | 0.743590 |
| 3     | 0.178900      | 0.287950        | 0.899749 | 0.818182 | 0.873786  | 0.769231 |
| 4     | 0.093100      | 0.345517        | 0.894737 | 0.820513 | 0.820513  | 0.820513 |
| 5     | 0.054500      | 0.434557        | 0.899749 | 0.826087 | 0.840708  | 0.811966 |
| 6     | 0.030900      | 0.487250        | 0.904762 | 0.827273 | 0.883495  | 0.777778 |
| 7     | 0.021700      | 0.494885        | 0.899749 | 0.830508 | 0.823529  | 0.837607 |
| 8     | 0.011500      | 0.580564        | 0.897243 | 0.814480 | 0.865385  | 0.769231 |
| 9     | 0.006000      | 0.604532        | 0.894737 | 0.820513 | 0.820513  | 0.820513 |
| 10    | 0.005000      | 0.616260        | 0.897243 | 0.822511 | 0.833333  | 0.811966 |

## How to Use

### As Text Classifier

```python
from transformers import pipeline

pretrained_name = "w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-2"

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
