---
language: id
tags:
  - indonesian-roberta-base-indolem-sentiment-classifier-fold-3
license: mit
datasets:
  - indolem
widget:
  - text: "Pelayanan hotel ini sangat baik."
---

## Indonesian RoBERTa Base IndoLEM Sentiment Classifier

Indonesian RoBERTa Base IndoLEM Sentiment Classifier is a sentiment-text-classification model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Indonesian RoBERTa Base](https://hf.co/flax-community/indonesian-roberta-base) model, which is then fine-tuned on [`indolem`](https://indolem.github.io/)'s [Sentiment Analysis](https://github.com/indolem/indolem/tree/main/sentiment) dataset consisting of Indonesian tweets and hotel reviews (Koto et al., 2020).

A 5-fold cross-validation experiment was performed, with splits provided by the original dataset authors. This model was trained on fold 0. You can find models trained on [fold 0](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-0), [fold 1](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-1), [fold 2](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-2), [fold 3](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-3), and [fold 4](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-4), in their respective links.

On **fold 3**, the model achieved an F1 of 82.61% on dev/validation and 85.27% on test. On all **5 folds**, the models achieved an average F1 of 84.14% on dev/validation and 84.64% on test.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                                                         | #params | Arch.        | Training/Validation data (text) |
| ------------------------------------------------------------- | ------- | ------------ | ------------------------------- |
| `indonesian-roberta-base-indolem-sentiment-classifier-fold-3` | 124M    | RoBERTa Base | `IndoLEM`'s Sentiment Analysis  |

## Evaluation Results

The model was trained for 10 epochs and the best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Accuracy | F1       | Precision | Recall   |
| ----- | ------------- | --------------- | -------- | -------- | --------- | -------- |
| 1     | 0.566700      | 0.446229        | 0.786967 | 0.593301 | 0.673913  | 0.529915 |
| 2     | 0.317200      | 0.288581        | 0.877193 | 0.810811 | 0.739437  | 0.897436 |
| 3     | 0.171500      | 0.342168        | 0.894737 | 0.800000 | 0.903226  | 0.717949 |
| 4     | 0.103200      | 0.349750        | 0.892231 | 0.817021 | 0.813559  | 0.820513 |
| 5     | 0.059600      | 0.486529        | 0.899749 | 0.826087 | 0.840708  | 0.811966 |
| 6     | 0.031800      | 0.543524        | 0.882206 | 0.808163 | 0.773438  | 0.846154 |
| 7     | 0.016200      | 0.564764        | 0.899749 | 0.819820 | 0.866667  | 0.777778 |
| 8     | 0.008300      | 0.593180        | 0.897243 | 0.819383 | 0.845455  | 0.794872 |
| 9     | 0.010000      | 0.631985        | 0.889724 | 0.810345 | 0.817391  | 0.803419 |
| 10    | 0.005500      | 0.646718        | 0.892231 | 0.813853 | 0.824561  | 0.803419 |

## How to Use

### As Text Classifier

```python
from transformers import pipeline

pretrained_name = "w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-3"

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
