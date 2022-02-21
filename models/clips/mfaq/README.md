---
pipeline_tag: sentence-similarity
license: apache-2.0
language:
- cs
- da
- de
- en
- es
- fi
- fr
- he
- hr
- hu
- id
- it
- nl
- 'no'
- pl
- pt
- ro
- ru
- sv
- tr
- vi
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
datasets:
- clips/mfaq
widget:
  source_sentence: "<Q>How many models can I host on HuggingFace?"
  sentences:
    - "<A>All plans come with unlimited private models and datasets."
    - "<A>AutoNLP is an automatic way to train and deploy state-of-the-art NLP models, seamlessly integrated with the Hugging Face ecosystem."
    - "<A>Based on how much training data and model variants are created, we send you a compute cost and payment link - as low as $10 per job."

---

# MFAQ

We present a multilingual FAQ retrieval model trained on the [MFAQ dataset](https://huggingface.co/datasets/clips/mfaq), it ranks candidate answers according to a given question.

## Installation

```
pip install sentence-transformers transformers
```

## Usage
You can use MFAQ with sentence-transformers or directly with a HuggingFace model. 
In both cases, questions need to be prepended with `<Q>`, and answers with `<A>`.

#### Sentence Transformers
```python
from sentence_transformers import SentenceTransformer

question = "<Q>How many models can I host on HuggingFace?"
answer_1 = "<A>All plans come with unlimited private models and datasets."
answer_2 = "<A>AutoNLP is an automatic way to train and deploy state-of-the-art NLP models, seamlessly integrated with the Hugging Face ecosystem."
answer_3 = "<A>Based on how much training data and model variants are created, we send you a compute cost and payment link - as low as $10 per job."

model = SentenceTransformer('clips/mfaq')
embeddings = model.encode([question, answer_1, answer_3, answer_3])
print(embeddings)
```

#### HuggingFace Transformers

```python
from transformers import AutoTokenizer, AutoModel
import torch

def mean_pooling(model_output, attention_mask):
    token_embeddings = model_output[0] #First element of model_output contains all token embeddings
    input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
    return torch.sum(token_embeddings * input_mask_expanded, 1) / torch.clamp(input_mask_expanded.sum(1), min=1e-9)

question = "<Q>How many models can I host on HuggingFace?"
answer_1 = "<A>All plans come with unlimited private models and datasets."
answer_2 = "<A>AutoNLP is an automatic way to train and deploy state-of-the-art NLP models, seamlessly integrated with the Hugging Face ecosystem."
answer_3 = "<A>Based on how much training data and model variants are created, we send you a compute cost and payment link - as low as $10 per job."

tokenizer = AutoTokenizer.from_pretrained('clips/mfaq')
model = AutoModel.from_pretrained('clips/mfaq')

# Tokenize sentences
encoded_input = tokenizer([question, answer_1, answer_3, answer_3], padding=True, truncation=True, return_tensors='pt')

# Compute token embeddings
with torch.no_grad():
    model_output = model(**encoded_input)

# Perform pooling. In this case, max pooling.
sentence_embeddings = mean_pooling(model_output, encoded_input['attention_mask'])
```

## Training
You can find the training script for the model [here](https://github.com/clips/mfaq).

## People
This model was developed by [Maxime De Bruyn](https://www.linkedin.com/in/maximedebruyn/), Ehsan Lotfi, Jeska Buhmann and Walter Daelemans.

## Citation information
```
@misc{debruyn2021mfaq,
      title={MFAQ: a Multilingual FAQ Dataset}, 
      author={Maxime De Bruyn and Ehsan Lotfi and Jeska Buhmann and Walter Daelemans},
      year={2021},
      eprint={2109.12870},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```