---
language: id
tags:
  - indonesian-roberta-base-indolem-sentiment-classifier-fold-1
license: mit
datasets:
  - indolem
widget:
  - text: "Pelayanan hotel ini sangat baik."
---

## Indonesian RoBERTa Base IndoLEM Sentiment Classifier

Indonesian RoBERTa Base IndoLEM Sentiment Classifier is a sentiment-text-classification model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Indonesian RoBERTa Base](https://hf.co/flax-community/indonesian-roberta-base) model, which is then fine-tuned on [`indolem`](https://indolem.github.io/)'s [Sentiment Analysis](https://github.com/indolem/indolem/tree/main/sentiment) dataset consisting of Indonesian tweets and hotel reviews (Koto et al., 2020).

A 5-fold cross-validation experiment was performed, with splits provided by the original dataset authors. This model was trained on fold 0. You can find models trained on [fold 0](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-0), [fold 1](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-1), [fold 2](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-2), [fold 3](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-3), and [fold 4](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-4), in their respective links.

On **fold 1**, the model achieved an F1 of 84.43% on dev/validation and 86.59% on test. On all **5 folds**, the models achieved an average F1 of 84.14% on dev/validation and 84.64% on test.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                                                         | #params | Arch.        | Training/Validation data (text) |
| ------------------------------------------------------------- | ------- | ------------ | ------------------------------- |
| `indonesian-roberta-base-indolem-sentiment-classifier-fold-1` | 124M    | RoBERTa Base | `IndoLEM`'s Sentiment Analysis  |

## Evaluation Results

The model was trained for 10 epochs and the best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Accuracy | F1       | Precision | Recall   |
| ----- | ------------- | --------------- | -------- | -------- | --------- | -------- |
| 1     | 0.563400      | 0.438638        | 0.771930 | 0.528497 | 0.671053  | 0.435897 |
| 2     | 0.313700      | 0.286461        | 0.857143 | 0.724638 | 0.833333  | 0.641026 |
| 3     | 0.179800      | 0.255090        | 0.892231 | 0.812227 | 0.830357  | 0.794872 |
| 4     | 0.092300      | 0.360222        | 0.897243 | 0.828452 | 0.811475  | 0.846154 |
| 5     | 0.054400      | 0.345958        | 0.904762 | 0.844262 | 0.811024  | 0.880342 |
| 6     | 0.026300      | 0.466914        | 0.902256 | 0.836820 | 0.819672  | 0.854701 |
| 7     | 0.018500      | 0.517265        | 0.904762 | 0.836207 | 0.843478  | 0.829060 |
| 8     | 0.009900      | 0.544317        | 0.902256 | 0.835443 | 0.825000  | 0.846154 |
| 9     | 0.008800      | 0.570152        | 0.904762 | 0.833333 | 0.855856  | 0.811966 |
| 10    | 0.007500      | 0.569749        | 0.902256 | 0.829694 | 0.848214  | 0.811966 |

## How to Use

### As Text Classifier

```python
from transformers import pipeline

pretrained_name = "w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-1"

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
