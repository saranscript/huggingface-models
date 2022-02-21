# DeCLUTR-sci-base

## Model description

This is the [allenai/scibert_scivocab_uncased](https://huggingface.co/allenai/scibert_scivocab_uncased) model, with extended pretraining on over 2 million scientific papers from [S2ORC](https://github.com/allenai/s2orc/) using the self-supervised training strategy presented in [DeCLUTR: Deep Contrastive Learning for Unsupervised Textual Representations](https://arxiv.org/abs/2006.03659).

## Intended uses & limitations

The model is intended to be used as a sentence encoder, similar to [Google's Universal Sentence Encoder](https://tfhub.dev/google/universal-sentence-encoder/4) or [Sentence Transformers](https://github.com/UKPLab/sentence-transformers). It is particularly suitable for scientific text.

#### How to use

Please see [our repo](https://github.com/JohnGiorgi/DeCLUTR) for full details. A simple example is shown below.

```python
import torch
from scipy.spatial.distance import cosine

from transformers import AutoModel, AutoTokenizer

# Load the model
tokenizer = AutoTokenizer.from_pretrained("johngiorgi/declutr-sci-base")
model = AutoModel.from_pretrained("johngiorgi/declutr-sci-base")

# Prepare some text to embed
text = [
    "Oncogenic KRAS mutations are common in cancer.",
    "Notably, c-Raf has recently been found essential for development of K-Ras-driven NSCLCs.",
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