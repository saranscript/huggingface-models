---
language: id
tags:
  - indonesian-roberta-base-sentiment-classifier
license: mit
datasets:
  - indonlu
widget:
  - text: "tidak jelek tapi keren"
---

## Indonesian RoBERTa Base Sentiment Classifier

Indonesian RoBERTa Base Sentiment Classifier is a sentiment-text-classification model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Indonesian RoBERTa Base](https://hf.co/flax-community/indonesian-roberta-base) model, which is then fine-tuned on [`indonlu`](https://hf.co/datasets/indonlu)'s `SmSA` dataset consisting of Indonesian comments and reviews.

After training, the model achieved an evaluation accuracy of 94.36% and F1-macro of 92.42%. On the benchmark test set, the model achieved an accuracy of 93.2% and F1-macro of 91.02%.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                                          | #params | Arch.        | Training/Validation data (text) |
| ---------------------------------------------- | ------- | ------------ | ------------------------------- |
| `indonesian-roberta-base-sentiment-classifier` | 124M    | RoBERTa Base | `SmSA`                          |

## Evaluation Results

The model was trained for 5 epochs and the best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Accuracy | F1       | Precision | Recall   |
| ----- | ------------- | --------------- | -------- | -------- | --------- | -------- |
| 1     | 0.342600      | 0.213551        | 0.928571 | 0.898539 | 0.909803  | 0.890694 |
| 2     | 0.190700      | 0.213466        | 0.934127 | 0.901135 | 0.925297  | 0.882757 |
| 3     | 0.125500      | 0.219539        | 0.942857 | 0.920901 | 0.927511  | 0.915193 |
| 4     | 0.083600      | 0.235232        | 0.943651 | 0.924227 | 0.926494  | 0.922048 |
| 5     | 0.059200      | 0.262473        | 0.942063 | 0.920583 | 0.924084  | 0.917351 |

## How to Use

### As Text Classifier

```python
from transformers import pipeline

pretrained_name = "sahri/sentiment"

nlp = pipeline(
    "sentiment-analysis",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("tidak jelek tapi keren")
```

## Disclaimer

Do consider the biases which come from both the pre-trained RoBERTa model and the `SmSA` dataset that may be carried over into the results of this model.

## Author

Indonesian RoBERTa Base Sentiment Classifier was trained and evaluated by [sahri ramadhan] All computation and development are done on Google Colaboratory using their free GPU access.
