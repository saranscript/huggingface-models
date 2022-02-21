---
language: "en"
tags:
- agriculture-domain
- agriculture
- fill-mask
widget:
- text: "[MASK] agriculture provides one of the most promising areas for innovation in green and blue infrastructure in cities."
---
# BERT for Agriculture Domain
A BERT-based language model further pre-trained from the checkpoint of [SciBERT](https://huggingface.co/allenai/scibert_scivocab_uncased).
The dataset gathered is a balance between scientific and general works in agriculture domain and encompassing knowledge from different areas of agriculture research and practical knowledge. 

The corpus contains 1.2 million paragraphs from National Agricultural Library (NAL) from the US Gov. and 5.3 million paragraphs from books and common literature from the **Agriculture Domain**.

The self-supervised learning approach of MLM was used to train the model.
- Masked language modeling (MLM): taking a sentence, the model randomly masks 15% of the words in the input then run
  the entire masked sentence through the model and has to predict the masked words. This is different from traditional
  recurrent neural networks (RNNs) that usually see the words one after the other, or from autoregressive models like
  GPT internally masks the future tokens. It allows the model to learn a bidirectional representation of the
  sentence.
```python
from transformers import pipeline
fill_mask = pipeline(
    "fill-mask",
    model="recobo/agriculture-bert-uncased",
    tokenizer="recobo/agriculture-bert-uncased"
)
fill_mask("[MASK] is the practice of cultivating plants and livestock.")
```