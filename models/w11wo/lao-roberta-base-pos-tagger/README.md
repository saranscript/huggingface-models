---
language: lo
tags:
  - lao-roberta-base-pos-tagger
license: mit
widget:
  - text: "ຮ້ອງ ມ່ວນ ແທ້ ສຽງດີ ອິຫຼີ"
---

## Lao RoBERTa Base POS Tagger

Lao RoBERTa Base POS Tagger is a part-of-speech token-classification model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Lao RoBERTa Base](https://huggingface.co/w11wo/lao-roberta-base) model, which is then fine-tuned on the [`Yunshan Cup 2020`](https://github.com/GKLMIP/Yunshan-Cup-2020) dataset consisting of tag-labelled Lao corpus.

After training, the model achieved an evaluation accuracy of 83.14%. On the benchmark test set, the model achieved an accuracy of 83.30%.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                         | #params | Arch.        | Training/Validation data (text) |
| ----------------------------- | ------- | ------------ | ------------------------------- |
| `lao-roberta-base-pos-tagger` | 124M    | RoBERTa Base | `Yunshan Cup 2020`              |

## Evaluation Results

The model was trained for 15 epochs, with a batch size of 8, a learning rate of 5e-5, with cosine annealing to 0. The best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Accuracy |
| ----- | ------------- | --------------- | -------- |
| 1     | 1.026100      | 0.733780        | 0.746021 |
| 2     | 0.646900      | 0.659625        | 0.775688 |
| 3     | 0.500400      | 0.576214        | 0.798523 |
| 4     | 0.385400      | 0.606503        | 0.805269 |
| 5     | 0.288000      | 0.652493        | 0.809092 |
| 6     | 0.204600      | 0.671678        | 0.815216 |
| 7     | 0.145200      | 0.704693        | 0.818209 |
| 8     | 0.098700      | 0.830561        | 0.816998 |
| 9     | 0.066100      | 0.883329        | 0.825232 |
| 10    | 0.043900      | 0.933347        | 0.825664 |
| 11    | 0.027200      | 0.992055        | 0.828449 |
| 12    | 0.017300      | 1.054874        | 0.830819 |
| 13    | 0.011500      | 1.081638        | 0.830940 |
| 14    | 0.008500      | 1.094252        | 0.831304 |
| 15    | 0.007400      | 1.097428        | 0.831442 |

## How to Use

### As Token Classifier

```python
from transformers import pipeline

pretrained_name = "w11wo/lao-roberta-base-pos-tagger"

nlp = pipeline(
    "token-classification",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("ຮ້ອງ ມ່ວນ ແທ້ ສຽງດີ ອິຫຼີ")
```

## Disclaimer

Do consider the biases which come from both the pre-trained RoBERTa model and the `Yunshan Cup 2020` dataset that may be carried over into the results of this model.

## Author

Lao RoBERTa Base POS Tagger was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.
