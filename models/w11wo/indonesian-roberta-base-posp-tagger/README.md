---
language: id
tags:
  - indonesian-roberta-base-posp-tagger
license: mit
datasets:
  - indonlu
widget:
  - text: "Budi sedang pergi ke pasar."
---

## Indonesian RoBERTa Base POSP Tagger

Indonesian RoBERTa Base POSP Tagger is a part-of-speech token-classification model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Indonesian RoBERTa Base](https://hf.co/flax-community/indonesian-roberta-base) model, which is then fine-tuned on [`indonlu`](https://hf.co/datasets/indonlu)'s `POSP` dataset consisting of tag-labelled news.

After training, the model achieved an evaluation F1-macro of 95.34%. On the benchmark test set, the model achieved an accuracy of 93.99% and F1-macro of 88.93%.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                                 | #params | Arch.        | Training/Validation data (text) |
| ------------------------------------- | ------- | ------------ | ------------------------------- |
| `indonesian-roberta-base-posp-tagger` | 124M    | RoBERTa Base | `POSP`                          |

## Evaluation Results

The model was trained for 10 epochs and the best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Precision | Recall   | F1       | Accuracy |
| ----- | ------------- | --------------- | --------- | -------- | -------- | -------- |
| 1     | 0.898400      | 0.343731        | 0.894324  | 0.894324 | 0.894324 | 0.894324 |
| 2     | 0.294700      | 0.236619        | 0.929620  | 0.929620 | 0.929620 | 0.929620 |
| 3     | 0.214100      | 0.202723        | 0.938349  | 0.938349 | 0.938349 | 0.938349 |
| 4     | 0.171100      | 0.183630        | 0.945264  | 0.945264 | 0.945264 | 0.945264 |
| 5     | 0.143300      | 0.169744        | 0.948469  | 0.948469 | 0.948469 | 0.948469 |
| 6     | 0.124700      | 0.174946        | 0.947963  | 0.947963 | 0.947963 | 0.947963 |
| 7     | 0.109800      | 0.167450        | 0.951590  | 0.951590 | 0.951590 | 0.951590 |
| 8     | 0.101300      | 0.163191        | 0.952475  | 0.952475 | 0.952475 | 0.952475 |
| 9     | 0.093500      | 0.163255        | 0.953361  | 0.953361 | 0.953361 | 0.953361 |
| 10    | 0.089000      | 0.164673        | 0.953445  | 0.953445 | 0.953445 | 0.953445 |

## How to Use

### As Token Classifier

```python
from transformers import pipeline

pretrained_name = "w11wo/indonesian-roberta-base-posp-tagger"

nlp = pipeline(
    "token-classification",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("Budi sedang pergi ke pasar.")
```

## Disclaimer

Do consider the biases which come from both the pre-trained RoBERTa model and the `POSP` dataset that may be carried over into the results of this model.

## Author

Indonesian RoBERTa Base POSP Tagger was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.