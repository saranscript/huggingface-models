---
pipeline_tag: sentence-similarity
language: fr
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
- fr
datasets:
- xnli
- stsb_multi_mt
---

# hugorosen/flaubert_base_uncased-xnli-sts

This is a [sentence-transformers](https://www.SBERT.net) model: It maps sentences & paragraphs to a 768 dimensional dense vector space and can be used for tasks like clustering or semantic search.

<!--- Describe your model here -->

## Usage (Sentence-Transformers)

Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer
sentences = ["Ceci est une phrase d'exemple", "Chaque phrase est convertie"]

model = SentenceTransformer('hugorosen/flaubert_base_uncased-xnli-sts')
embeddings = model.encode(sentences)
print(embeddings)
```



## Usage (HuggingFace Transformers)
Without [sentence-transformers](https://www.SBERT.net), you can use the model like this: First, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.

```python
from transformers import AutoTokenizer, AutoModel
import torch


#Mean Pooling - Take attention mask into account for correct averaging
def mean_pooling(model_output, attention_mask):
    token_embeddings = model_output[0] #First element of model_output contains all token embeddings
    input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
    return torch.sum(token_embeddings * input_mask_expanded, 1) / torch.clamp(input_mask_expanded.sum(1), min=1e-9)


# Sentences we want sentence embeddings for
sentences = ["Ceci est une phrase d'exemple", "Chaque phrase est convertie"]

# Load model from HuggingFace Hub
tokenizer = AutoTokenizer.from_pretrained('hugorosen/flaubert_base_uncased-xnli-sts')
model = AutoModel.from_pretrained('hugorosen/flaubert_base_uncased-xnli-sts')

# Tokenize sentences
encoded_input = tokenizer(sentences, padding=True, truncation=True, return_tensors='pt')

# Compute token embeddings
with torch.no_grad():
    model_output = model(**encoded_input)

# Perform pooling. In this case, mean pooling.
sentence_embeddings = mean_pooling(model_output, encoded_input['attention_mask'])

print("Sentence embeddings:")
print(sentence_embeddings)
```



## Evaluation Results

<!--- Describe how your model was evaluated -->

This model scores 76.9% on STS test (french)


## Training
### Pre-training

We use the pre-trained [flaubert/flaubert_base_uncased](https://huggingface.co/flaubert/flaubert_base_cased). Please refer to the model card for more detailed information about the pre-training procedure.

### Fine-tuning

we fine-tune the model using a `CosineSimilarityLoss` on XNLI and STS dataset (french).

Parameters of the fit()-Method:
```
{
    "epochs": 4,
    "evaluation_steps": 1000,
    "evaluator": "sentence_transformers.evaluation.EmbeddingSimilarityEvaluator.EmbeddingSimilarityEvaluator",
    "max_grad_norm": 1,
    "optimizer_class": "<class 'transformers.optimization.AdamW'>",
    "optimizer_params": {
        "lr": 2e-05
    },
    "scheduler": "WarmupLinear",
    "steps_per_epoch": null,
    "warmup_steps": 144,
    "weight_decay": 0.01
}
```


## Full Model Architecture
```
SentenceTransformer(
  (0): Transformer({'max_seq_length': 128, 'do_lower_case': False}) with Transformer model: FlaubertModel 
  (1): Pooling({'word_embedding_dimension': 768, 'pooling_mode_cls_token': False, 'pooling_mode_mean_tokens': True, 'pooling_mode_max_tokens': False, 'pooling_mode_mean_sqrt_len_tokens': False})
)
```

## Citing & Authors

Fine-tuned for semantic similarity by Hugo Rosenkranz-costa.

Based on FlauBERT:

```
@InProceedings{le2020flaubert,
  author    = {Le, Hang  and  Vial, Lo\"{i}c  and  Frej, Jibril  and  Segonne, Vincent  and  Coavoux, Maximin  and  Lecouteux, Benjamin  and  Allauzen, Alexandre  and  Crabb\'{e}, Beno\^{i}t  and  Besacier, Laurent  and  Schwab, Didier},
  title     = {FlauBERT: Unsupervised Language Model Pre-training for French},
  booktitle = {Proceedings of The 12th Language Resources and Evaluation Conference},
  month     = {May},
  year      = {2020},
  address   = {Marseille, France},
  publisher = {European Language Resources Association},
  pages     = {2479--2490},
  url       = {https://www.aclweb.org/anthology/2020.lrec-1.302}
}
```