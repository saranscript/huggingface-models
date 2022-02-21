---
language: en
license: apache-2.0
datasets:
- bookcorpus
- wikipedia
- cc_news
---

# BigBird base model

BigBird, is a sparse-attention based transformer which extends Transformer based models, such as BERT to much longer sequences. Moreover, BigBird comes along with a theoretical understanding of the capabilities of a complete transformer that the sparse model can handle.

It is a pretrained model on English language using a masked language modeling (MLM) objective. It was introduced in this [paper](https://arxiv.org/abs/2007.14062) and first released in this [repository](https://github.com/google-research/bigbird).

Disclaimer: The team releasing BigBird did not write a model card for this model so this model card has been written by the Hugging Face team.

## Model description

BigBird relies on **block sparse attention** instead of normal attention (i.e. BERT's attention) and can handle sequences up to a length of 4096 at a much lower compute cost compared to BERT. It has achieved SOTA on various tasks involving very long sequences such as long documents summarization, question-answering with long contexts.

## How to use `TODO: Update`

Here is how to use this model to get the features of a given text in Flax:

```python
from transformers import BigBirdTokenizer, FlaxBigBirdModel

model_id = "flax-community/bigband"

# by default its in `block_sparse` mode with num_random_blocks=3, block_size=64
model = FlaxBigBirdModel.from_pretrained(model_id)

# you can change `attention_type` to full attention like this:
model = FlaxBigBirdModel.from_pretrained(model_id, attention_type="original_full")

# you can change `block_size` & `num_random_blocks` like this:
model = FlaxBigBirdModel.from_pretrained(model_id, block_size=16, num_random_blocks=2)

tokenizer = BigBirdTokenizer.from_pretrained(model_id)

text = "Replace me by any text you'd like."
inputs = tokenizer(text, return_tensors="jax")
output = model(**inputs)
```

## Training Data `TODO: Update`

This model is pre-trained on four publicly available datasets: **Books**, **CC-News**, **Stories** and **Wikipedia**. It used same sentencepiece vocabulary as RoBERTa (which is in turn borrowed from GPT2).

## Training Procedure `TODO: Update`

Document longer than 4096 were split into multiple documents and documents that were much smaller than 4096 were joined. Following the original BERT training, 15% of tokens were masked and model is trained to predict the mask.

Model is warm started from RoBERTa’s checkpoint.
