---
pipeline_tag: sentence-similarity
license: apache-2.0
tags:
- text2vec
- feature-extraction
- sentence-similarity
- transformers
---
# shibing624/text2vec
This is a CoSENT(Cosine Sentence) model: It maps sentences to a 768 dimensional dense vector space and can be used for tasks like clustering or semantic search.
## Usage (text2vec)
Using this model becomes easy when you have [text2vec](https://github.com/shibing624/text2vec) installed:
```
pip install -U text2vec
```
Then you can use the model like this:
```python
from text2vec import SBert
sentences = ['如何更换花呗绑定银行卡', '花呗更改绑定银行卡']

model = SBert('shibing624/text2vec-base-chinese')
embeddings = model.encode(sentences)
print(embeddings)
```
## Usage (HuggingFace Transformers)
Without [text2vec](https://github.com/shibing624/text2vec), you can use the model like this: First, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.
```python
from transformers import BertTokenizer, BertModel
import torch

# Mean Pooling - Take attention mask into account for correct averaging
def mean_pooling(model_output, attention_mask):
    token_embeddings = model_output[0]  # First element of model_output contains all token embeddings
    input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
    return torch.sum(token_embeddings * input_mask_expanded, 1) / torch.clamp(input_mask_expanded.sum(1), min=1e-9)

# Load model from HuggingFace Hub
tokenizer = BertTokenizer.from_pretrained('shibing624/text2vec-base-chinese')
model = BertModel.from_pretrained('shibing624/text2vec-base-chinese')
sentences = ['如何更换花呗绑定银行卡', '花呗更改绑定银行卡']
# Tokenize sentences
encoded_input = tokenizer(sentences, padding=True, truncation=True, return_tensors='pt')

# Compute token embeddings
with torch.no_grad():
    model_output = model(**encoded_input)
# Perform pooling. In this case, max pooling.
sentence_embeddings = mean_pooling(model_output, encoded_input['attention_mask'])
print("Sentence embeddings:")
print(sentence_embeddings)
```
## Evaluation Results
For an automated evaluation of this model, see the *Sentence Embeddings Benchmark*: [text2vec](https://github.com/shibing624/text2vec)

## Full Model Architecture
```
CoSENT(
  (0): Transformer({'max_seq_length': 128, 'do_lower_case': False}) with Transformer model: BertModel 
  (1): Pooling({'word_embedding_dimension': 768, 'pooling_mode_mean_tokens': True})
)
```
## Citing & Authors
This model was trained by [text2vec/cosent](https://github.com/shibing624/text2vec/tree/master/text2vec/cosent). 
        
If you find this model helpful, feel free to cite:
```bibtex 
@software{text2vec,
  author = {Xu Ming},
  title = {text2vec: A Tool for Text to Vector},
  year = {2022},
  url = {https://github.com/shibing624/text2vec},
}
```
