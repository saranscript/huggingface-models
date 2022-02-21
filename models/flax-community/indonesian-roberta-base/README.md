---
language: id
tags:
  - indonesian-roberta-base
license: mit
datasets:
  - oscar
widget:
  - text: "Budi telat ke sekolah karena ia <mask>."
---

## Indonesian RoBERTa Base

Indonesian RoBERTa Base is a masked language model based on the [RoBERTa](https://arxiv.org/abs/1907.11692) model. It was trained on the [OSCAR](https://huggingface.co/datasets/oscar) dataset, specifically the `unshuffled_deduplicated_id` subset. The model was trained from scratch and achieved an evaluation loss of 1.798 and an evaluation accuracy of 62.45%.

This model was trained using HuggingFace's Flax framework and is part of the [JAX/Flax Community Week](https://discuss.huggingface.co/t/open-to-the-community-community-week-using-jax-flax-for-nlp-cv/7104) organized by HuggingFace. All training was done on a TPUv3-8 VM, sponsored by the Google Cloud team.

All necessary scripts used for training could be found in the [Files and versions](https://huggingface.co/flax-community/indonesian-roberta-base/tree/main) tab, as well as the [Training metrics](https://huggingface.co/flax-community/indonesian-roberta-base/tensorboard) logged via Tensorboard.

## Model

| Model                     | #params | Arch.   | Training/Validation data (text)            |
| ------------------------- | ------- | ------- | ------------------------------------------ |
| `indonesian-roberta-base` | 124M    | RoBERTa | OSCAR `unshuffled_deduplicated_id` Dataset |

## Evaluation Results

The model was trained for 8 epochs and the following is the final result once the training ended.

| train loss | valid loss | valid accuracy | total time |
| ---------- | ---------- | -------------- | ---------- |
| 1.870      | 1.798      | 0.6245         | 18:25:39   |

## How to Use

### As Masked Language Model

```python
from transformers import pipeline

pretrained_name = "flax-community/indonesian-roberta-base"

fill_mask = pipeline(
    "fill-mask",
    model=pretrained_name,
    tokenizer=pretrained_name
)

fill_mask("Budi sedang <mask> di sekolah.")
```

### Feature Extraction in PyTorch

```python
from transformers import RobertaModel, RobertaTokenizerFast

pretrained_name = "flax-community/indonesian-roberta-base"
model = RobertaModel.from_pretrained(pretrained_name)
tokenizer = RobertaTokenizerFast.from_pretrained(pretrained_name)

prompt = "Budi sedang berada di sekolah."
encoded_input = tokenizer(prompt, return_tensors='pt')
output = model(**encoded_input)
```

## Team Members

- Wilson Wongso ([@w11wo](https://hf.co/w11wo))
- Steven Limcorn ([@stevenlimcorn](https://hf.co/stevenlimcorn))
- Samsul Rahmadani ([@munggok](https://hf.co/munggok))
- Chew Kok Wah ([@chewkokwah](https://hf.co/chewkokwah))