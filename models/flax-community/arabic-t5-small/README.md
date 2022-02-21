---
language:
  - ar
datasets:
  - mc4
  - oscar
  - arabic_billion_words
---

# arabic-t5-small

This is a T5v1.1 (small) trained on the concatenation of the Arabic Billion Words corpus and the Arabic subsets of the mC4 and Oscar datasets.

The model could only be trained for about `10%` of the whole dataset due to time limitations. This is equivalent to `22'000` steps or about `4.3` Billion tokens.

## Training parameters

|                       |               |
| :-------------------: | :-----------: |
|  Training batch size  |     `384`     |
| Evaluation batch size |     `768`     |
|     learning rate     |    `1e-2`     |
|         dtype         | `jnp.float32` |

## Preprocessing and the tokenizer

We tried to keep the preprocessing to a bare minimum. We only replaced URLs, emails and social media user mentions with fixed tokens.

Contrary to other pretrained Arabic LMs, we decided to not strip the Arabic diacritics and to keep them part of the vocabulary.

The tokenizer was trained on `5%` of the training set, with a vocabulary size of `64'000`.

For more details about preprocessing, check the [tokenizer code](https://huggingface.co/flax-community/arabic-t5-small/blob/main/t5_tokenizer_model.py)

## Data

The model was trained on the concatenation of the Arabic Billion Words corpus and the Arabic subsets of the mC4 and Oscar datasets.

A random `0.1%` subset of the data was reserved for evaluation and the rest for training.

## Results

|                     |               |
| :-----------------: | :-----------: |
| Evaluation accuracy |   `56.84%`    |
|   Evaluation Loss   |    `2.423`    |
|    Training Loss    |    `2.392`    |
|    Training Time    | `22h 23m 51s` |

## Note for finetuning

This model was pretrained with dropout turned off, so the default `dropout_rate` in the model config is `0`.
To finetune the model dropout should be turned be back on, like this:

```python
model = T5ForConditionalGeneration.from_pretrained("flax-community/arabic-t5-small", dropout_rate=0.1)
```

or,

```python
model = AutoModelForSeq2SeqLM.from_pretrained("flax-community/arabic-t5-small", dropout_rate=0.1)
```
