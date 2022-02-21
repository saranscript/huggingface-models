 
---
language:
- el
tags:
- pytorch
- causal-lm
widget:
- text: "Το αγαπημένο μου μέρος είναι"
license: apache-2.0


---

# Greek (el) GPT2 model
<img src="https://huggingface.co/lighteternal/gpt2-finetuned-greek-small/raw/main/GPT2el.png" width="600"/>

### By the Hellenic Army Academy (SSE) and the Technical University of Crete (TUC)

* language: el
* licence: apache-2.0
* dataset: ~23.4 GB of Greek corpora 
* model: GPT2 (12-layer, 768-hidden, 12-heads, 117M parameters. OpenAI GPT-2 English model, finetuned for the Greek language)
* pre-processing: tokenization + BPE segmentation
* metrics: perplexity

### Model description

A text generation (autoregressive) model, using Huggingface transformers and fastai based on the English GPT-2.  
Finetuned with gradual layer unfreezing. This is a more efficient and sustainable alternative compared to training from scratch, especially for low-resource languages.  
Based on the work of Thomas Dehaene (ML6) for the creation of a Dutch GPT2: https://colab.research.google.com/drive/1Y31tjMkB8TqKKFlZ5OJ9fcMp3p8suvs4?usp=sharing


### How to use

```
from transformers import pipeline

model = "lighteternal/gpt2-finetuned-greek"

generator = pipeline(
    'text-generation',
    device=0,
    model=f'{model}',
    tokenizer=f'{model}')
    
text = "Μια φορά κι έναν καιρό"

print("\
".join([x.get("generated_text") for x in generator(
    text,
    max_length=len(text.split(" "))+15,
    do_sample=True,
    top_k=50,
    repetition_penalty = 1.2,
    add_special_tokens=False,
    num_return_sequences=5,
    temperature=0.95,
    top_p=0.95)]))
    
```


## Training data

We used a 23.4GB sample from a consolidated Greek corpus from CC100, Wikimatrix, Tatoeba, Books, SETIMES and GlobalVoices containing long senquences.
This is a better version of our GPT-2 small model (https://huggingface.co/lighteternal/gpt2-finetuned-greek-small)


## Metrics

| Metric      | Value |
| ----------- | ----------- |
| Train Loss | 3.67 |
| Validation Loss | 3.83 |
| Perplexity  | 39.12 |


### Acknowledgement

The research work was supported by the Hellenic Foundation for Research and Innovation (HFRI) under the HFRI PhD Fellowship grant (Fellowship Number:50, 2nd call)

Based on the work of Thomas Dehaene (ML6): https://blog.ml6.eu/dutch-gpt2-autoregressive-language-modelling-on-a-budget-cff3942dd020
