---
language: id
tags:
  - indonesian-roberta-base-indolem-sentiment-classifier-fold-4
license: mit
datasets:
  - indolem
widget:
  - text: "Pelayanan hotel ini sangat baik."
---

## Indonesian RoBERTa Base IndoLEM Sentiment Classifier

Indonesian RoBERTa Base IndoLEM Sentiment Classifier is a sentiment-text-classification model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Indonesian RoBERTa Base](https://hf.co/flax-community/indonesian-roberta-base) model, which is then fine-tuned on [`indolem`](https://indolem.github.io/)'s [Sentiment Analysis](https://github.com/indolem/indolem/tree/main/sentiment) dataset consisting of Indonesian tweets and hotel reviews (Koto et al., 2020).

A 5-fold cross-validation experiment was performed, with splits provided by the original dataset authors. This model was trained on fold 0. You can find models trained on [fold 0](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-0), [fold 1](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-1), [fold 2](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-2), [fold 3](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-3), and [fold 4](https://huggingface.co/w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-4), in their respective links.

On **fold 4**, the model achieved an F1 of 84.21% on dev/validation and 85.36% on test. On all **5 folds**, the models achieved an average F1 of 84.14% on dev/validation and 84.64% on test.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                                                         | #params | Arch.        | Training/Validation data (text) |
| ------------------------------------------------------------- | ------- | ------------ | ------------------------------- |
| `indonesian-roberta-base-indolem-sentiment-classifier-fold-4` | 124M    | RoBERTa Base | `IndoLEM`'s Sentiment Analysis  |

## Evaluation Results

The model was trained for 10 epochs and the best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Accuracy | F1       | Precision | Recall   |
| ----- | ------------- | --------------- | -------- | -------- | --------- | -------- |
| 1     | 0.565600      | 0.441932        | 0.771930 | 0.542714 | 0.658537  | 0.461538 |
| 2     | 0.303300      | 0.302146        | 0.869674 | 0.785124 | 0.760000  | 0.811966 |
| 3     | 0.175300      | 0.337158        | 0.879699 | 0.769231 | 0.879121  | 0.683761 |
| 4     | 0.084000      | 0.343521        | 0.894737 | 0.815789 | 0.837838  | 0.794872 |
| 5     | 0.036700      | 0.511235        | 0.889724 | 0.821138 | 0.782946  | 0.863248 |
| 6     | 0.020300      | 0.628374        | 0.897243 | 0.812785 | 0.872549  | 0.760684 |
| 7     | 0.019400      | 0.609241        | 0.909774 | 0.842105 | 0.864865  | 0.820513 |
| 8     | 0.005400      | 0.623904        | 0.897243 | 0.825532 | 0.822034  | 0.829060 |
| 9     | 0.005300      | 0.641695        | 0.904762 | 0.836207 | 0.843478  | 0.829060 |
| 10    | 0.003900      | 0.645317        | 0.904762 | 0.836207 | 0.843478  | 0.829060 |

## How to Use

### As Text Classifier

```python
from transformers import pipeline

pretrained_name = "w11wo/indonesian-roberta-base-indolem-sentiment-classifier-fold-4"

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
