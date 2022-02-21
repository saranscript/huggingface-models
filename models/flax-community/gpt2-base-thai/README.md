---
language: th
tags:
  - gpt2-base-thai
license: mit
datasets:
  - oscar
widget:
  - text: "สวัสดีตอนเช้า"
---

## GPT-2 Base Thai

GPT-2 Base Thai is a causal language model based on the [OpenAI GPT-2](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf) model. It was trained on the [OSCAR](https://huggingface.co/datasets/oscar) dataset, specifically the `unshuffled_deduplicated_th` subset. The model was trained from scratch and achieved an evaluation loss of 1.708 and an evaluation perplexity of 5.516.

This model was trained using HuggingFace's Flax framework and is part of the [JAX/Flax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) organized by HuggingFace. All training was done on a TPUv3-8 VM, sponsored by the Google Cloud team.

All necessary scripts used for training could be found in the [Files and versions](https://hf.co/flax-community/gpt2-base-thai/tree/main) tab, as well as the [Training metrics](https://hf.co/flax-community/gpt2-base-thai/tensorboard) logged via Tensorboard.

## Model

| Model            | #params | Arch. | Training/Validation data (text)      |
| ---------------- | ------- | ----- | ------------------------------------ |
| `gpt2-base-thai` | 124M    | GPT-2 | `unshuffled_deduplicated_th` Dataset |

## Evaluation Results

The model was trained for 3 epochs and the following is the final result once the training ended.

| train loss | valid loss | valid PPL | total time |
| ---------- | ---------- | --------- | ---------- |
| 1.638      | 1.708      | 5.516     | 6:12:34    |

## How to Use

### As Causal Language Model

```python
from transformers import pipeline

pretrained_name = "flax-community/gpt2-base-thai"

nlp = pipeline(
    "text-generation",
    model=pretrained_name,
    tokenizer=pretrained_name
)

nlp("สวัสดีตอนเช้า")
```

### Feature Extraction in PyTorch

```python
from transformers import GPT2Model, GPT2TokenizerFast

pretrained_name = "flax-community/gpt2-base-thai"
model = GPT2Model.from_pretrained(pretrained_name)
tokenizer = GPT2TokenizerFast.from_pretrained(pretrained_name)

prompt = "สวัสดีตอนเช้า"
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Team Members

- Sakares Saengkaew ([@sakares](https://hf.co/sakares))
- Wilson Wongso ([@w11wo](https://hf.co/w11wo))
