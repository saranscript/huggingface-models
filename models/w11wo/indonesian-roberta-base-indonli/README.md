---
language: id
tags:
  - indonesian-roberta-base-indonli
license: mit
datasets:
  - indonli
widget:
  - text: "Andi tersenyum karena mendapat hasil baik. </s></s> Andi sedih."
---

## Indonesian RoBERTa Base IndoNLI

Indonesian RoBERTa Base IndoNLI is a natural language inference (NLI) model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. The model was originally the pre-trained [Indonesian RoBERTa Base](https://hf.co/flax-community/indonesian-roberta-base) model, which is then fine-tuned on [`IndoNLI`](https://github.com/ir-nlp-csui/indonli)'s dataset consisting of Indonesian Wikipedia, news, and Web articles [1].

After training, the model achieved an evaluation/dev accuracy of 77.06%. On the benchmark `test_lay` subset, the model achieved an accuracy of 74.24% and on the benchmark `test_expert` subset, the model achieved an accuracy of 61.66%.

Hugging Face's `Trainer` class from the [Transformers](https://huggingface.co/transformers) library was used to train the model. PyTorch was used as the backend framework during training, but the model remains compatible with other frameworks nonetheless.

## Model

| Model                             | #params | Arch.        | Training/Validation data (text) |
| --------------------------------- | ------- | ------------ | ------------------------------- |
| `indonesian-roberta-base-indonli` | 124M    | RoBERTa Base | `IndoNLI`                       |

## Evaluation Results

The model was trained for 5 epochs, with a batch size of 16, a learning rate of 2e-5, a weight decay of 0.1, and a warmup ratio of 0.2, with linear annealing to 0. The best model was loaded at the end.

| Epoch | Training Loss | Validation Loss | Accuracy |
| ----- | ------------- | --------------- | -------- |
| 1     | 0.989200      | 0.691663        | 0.731452 |
| 2     | 0.673000      | 0.621913        | 0.766045 |
| 3     | 0.449900      | 0.662543        | 0.770596 |
| 4     | 0.293600      | 0.777059        | 0.768320 |
| 5     | 0.194200      | 0.948068        | 0.764224 |

## How to Use

### As NLI Classifier

```python
from transformers import pipeline

pretrained_name = "w11wo/indonesian-roberta-base-indonli"

nlp = pipeline(
    "sentiment-analysis",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("Andi tersenyum karena mendapat hasil baik. </s></s> Andi sedih.")
```

## Disclaimer

Do consider the biases which come from both the pre-trained RoBERTa model and the `IndoNLI` dataset that may be carried over into the results of this model.

## References

[1] Mahendra, R., Aji, A. F., Louvan, S., Rahman, F., & Vania, C. (2021, November). [IndoNLI: A Natural Language Inference Dataset for Indonesian](https://arxiv.org/abs/2110.14566). _Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing_. Association for Computational Linguistics.

## Author

Indonesian RoBERTa Base IndoNLI was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.
