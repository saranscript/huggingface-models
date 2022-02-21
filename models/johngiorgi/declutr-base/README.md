# DeCLUTR-base

## Model description

The "DeCLUTR-base" model from our paper: [DeCLUTR: Deep Contrastive Learning for Unsupervised Textual Representations](https://arxiv.org/abs/2006.03659).

## Intended uses & limitations

The model is intended to be used as a universal sentence encoder, similar to [Google's Universal Sentence Encoder](https://tfhub.dev/google/universal-sentence-encoder/4) or [Sentence Transformers](https://github.com/UKPLab/sentence-transformers).

#### How to use

Please see [our repo](https://github.com/JohnGiorgi/DeCLUTR) for full details. A simple example is shown below.

```python
import torch
from scipy.spatial.distance import cosine

from transformers import AutoModel, AutoTokenizer

# Load the model
tokenizer = AutoTokenizer.from_pretrained("johngiorgi/declutr-base")
model = AutoModel.from_pretrained("johngiorgi/declutr-base")

# Prepare some text to embed
text = [
    "A smiling costumed woman is holding an umbrella.",
    "A happy woman in a fairy costume holds an umbrella.",
]
inputs = tokenizer(text, padding=True, truncation=True, return_tensors="pt")

# Embed the text
with torch.no_grad():
    sequence_output = model(**inputs)[0]

# Mean pool the token-level embeddings to get sentence-level embeddings
embeddings = torch.sum(
    sequence_output * inputs["attention_mask"].unsqueeze(-1), dim=1
) / torch.clamp(torch.sum(inputs["attention_mask"], dim=1, keepdims=True), min=1e-9)

# Compute a semantic similarity via the cosine distance
semantic_sim = 1 - cosine(embeddings[0], embeddings[1])
```

### BibTeX entry and citation info

```bibtex
@article{Giorgi2020DeCLUTRDC,
  title={DeCLUTR: Deep Contrastive Learning for Unsupervised Textual Representations},
  author={John M Giorgi and Osvald Nitski and Gary D. Bader and Bo Wang},
  journal={ArXiv},
  year={2020},
  volume={abs/2006.03659}
}
```