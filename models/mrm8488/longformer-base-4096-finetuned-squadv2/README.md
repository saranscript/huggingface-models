---
language: en
datasets:
- squad_v2
tags:
- QA
- long context
- Q&A
---

# Longformer-base-4096 fine-tuned on SQuAD v2

[Longformer-base-4096 model](https://huggingface.co/allenai/longformer-base-4096) fine-tuned on [SQuAD v2](https://rajpurkar.github.io/SQuAD-explorer/) for **Q&A** downstream task.

## Longformer-base-4096

[Longformer](https://arxiv.org/abs/2004.05150) is a transformer model for long documents. 

`longformer-base-4096` is a BERT-like model started from the RoBERTa checkpoint and pretrained for MLM on long documents. It supports sequences of length up to 4,096. 
 
Longformer uses a combination of a sliding window (local) attention and global attention. Global attention is user-configured based on the task to allow the model to learn task-specific representations.

## Details of the downstream task (Q&A) - Dataset 📚 🧐 ❓

Dataset ID: ```squad_v2``` from  [HuggingFace/Datasets](https://github.com/huggingface/datasets)

| Dataset  | Split | # samples |
| -------- | ----- | --------- |
| squad_v2 | train | 130319     |
| squad_v2 | valid  | 11873     |

How to load it from [datasets](https://github.com/huggingface/datasets)

```python
!pip install datasets
from datasets import load_dataset
dataset = load_dataset('squad_v2')
```

Check out more about this dataset and others in [Datasets Viewer](https://huggingface.co/datasets/viewer/)


## Model fine-tuning 🏋️‍

The training script is a slightly modified version of [this one](https://colab.research.google.com/drive/1zEl5D-DdkBKva-DdreVOmN0hrAfzKG1o?usp=sharing)



## Model in Action 🚀

```python
import torch
from transformers import AutoTokenizer, AutoModelForQuestionAnswering
ckpt = "mrm8488/longformer-base-4096-finetuned-squadv2"
tokenizer = AutoTokenizer.from_pretrained(ckpt)
model = AutoModelForQuestionAnswering.from_pretrained(ckpt)

text = "Huggingface has democratized NLP. Huge thanks to Huggingface for this."
question = "What has Huggingface done ?"
encoding = tokenizer(question, text, return_tensors="pt")
input_ids = encoding["input_ids"]

# default is local attention everywhere
# the forward method will automatically set global attention on question tokens
attention_mask = encoding["attention_mask"]

start_scores, end_scores = model(input_ids, attention_mask=attention_mask)
all_tokens = tokenizer.convert_ids_to_tokens(input_ids[0].tolist())

answer_tokens = all_tokens[torch.argmax(start_scores) :torch.argmax(end_scores)+1]
answer = tokenizer.decode(tokenizer.convert_tokens_to_ids(answer_tokens))

# output => democratized NLP
```

## Usage with HF `pipleine`
```python
from transformers import AutoTokenizer, AutoModelForQuestionAnswering, pipeline

ckpt = "mrm8488/longformer-base-4096-finetuned-squadv2"
tokenizer = AutoTokenizer.from_pretrained(ckpt)
model = AutoModelForQuestionAnswering.from_pretrained(ckpt)

qa = pipeline({"question-answering", model=model, tokenizer=tokenizer)

text = "Huggingface has democratized NLP. Huge thanks to Huggingface for this."
question = "What has Huggingface done?"

qa({"question": question, "context": text})
```

If given the same context we ask something that is not there, the output for **no answer** will be ```<s>```

> Created by [Manuel Romero/@mrm8488](https://twitter.com/mrm8488) | [LinkedIn](https://www.linkedin.com/in/manuel-romero-cs/)

> Made with <span style="color: #e25555;">&hearts;</span> in Spain

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Y8Y3VYYE)
