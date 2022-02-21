# Cross-Encoder for QNLI

This model was trained using [SentenceTransformers](https://sbert.net) [Cross-Encoder](https://www.sbert.net/examples/applications/cross-encoder/README.html) class.

This model uses [electra-base](https://huggingface.co/google/electra-base-discriminator).

## Training Data

Given a question and paragraph, can the question be answered by the paragraph? The models have been trained on the [GLUE QNLI](https://arxiv.org/abs/1804.07461) dataset, which transformed the [SQuAD dataset](https://rajpurkar.github.io/SQuAD-explorer/) into an NLI task.

## Usage and Performance

Pre-trained models can be used like this:
```python
from sentence_transformers import CrossEncoder

model = CrossEncoder('model_name')
scores = model.predict([('Query', 'Paragraph1'), ('Query', 'Paragraph2')])

print(scores)
```
