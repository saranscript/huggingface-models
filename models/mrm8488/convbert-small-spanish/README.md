---
language: es
datasets:
- large_spanish_corpus
license: mit
---

# ConvBERT small pre-trained on large_spanish_corpus

The ConvBERT architecture is presented in the ["ConvBERT: Improving BERT with Span-based Dynamic Convolution"](https://arxiv.org/abs/2008.02496) paper.

## Metrics on evaluation set

```
disc_accuracy = 0.95163906
disc_auc = 0.9405496
disc_loss = 0.13658184
disc_precision = 0.80829453
disc_recall = 0.49316448
global_step = 1000000
loss = 9.12079
masked_lm_accuracy = 0.53505784
masked_lm_loss = 2.3028736
sampled_masked_lm_accuracy = 0.44047198
```

## Usage

```python
from transformers import AutoModel, AutoTokenizer
model_name = "mrm8488/convbert-small-spanish"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModel.from_pretrained(model_name)
```

> Created by [Manuel Romero/@mrm8488](https://twitter.com/mrm8488) with the support of [Narrativa](https://www.narrativa.com/)

> Made with <span style="color: #e25555;">&hearts;</span> in Spain