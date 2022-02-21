# Cross-Encoder for MS Marco

This model was trained using [SentenceTransformers](https://sbert.net) [Cross-Encoder](https://www.sbert.net/examples/applications/cross-encoder/README.html) class.

This model uses [electra-base](https://huggingface.co/google/electra-base-discriminator).

## Training Data

This model was trained on the [MS Marco Passage Ranking](https://github.com/microsoft/MSMARCO-Passage-Ranking) dataset. The model will predict a score between 0 and 1: Given a question and paragraph, can the question be answered by the paragraph?.

## Usage and Performance

Pre-trained models can be used like this:
```python
from sentence_transformers import CrossEncoder

model = CrossEncoder('model_name')
scores = model.predict([('Query', 'Paragraph1'), ('Query', 'Paragraph2')])

print(scores)
```
