---
language: es
thumbnail: https://imgur.com/a/G77ZqQN
pipeline_tag: sentence-similarity
datasets:
- stsb_multi_mt
tags:
- sentence-transformers
- feature-extraction
- sentence-similarity
- transformers
---

# Distiluse-m-v2 fine-tuned on stsb_multi_mt for Spanish Semantic Textual Similarity

This is a [sentence-transformers](https://www.SBERT.net) model (distiluse-base-multilingual-cased-v2): It maps sentences & paragraphs to a 768 dimensional dense vector space and can be used for tasks like clustering or semantic search.

<!--- Describe your model here -->

## Usage (Sentence-Transformers)

Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer
sentences = ["Nerea va a comprar un cuadro usando bitcoins", "Se puede comprar arte con bitcoins"]

model = SentenceTransformer('mrm8488/distiluse-base-multilingual-cased-v2-finetuned-stsb_multi_mt-es')
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
sentences = ['This is an example sentence', 'Each sentence is converted']

# Load model from HuggingFace Hub
tokenizer = AutoTokenizer.from_pretrained('mrm8488/distiluse-base-multilingual-cased-v2-finetuned-stsb_multi_mt-es')
model = AutoModel.from_pretrained('mrm8488/distiluse-base-multilingual-cased-v2-finetuned-stsb_multi_mt-es')

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

## How to evaluate

```py
from datasets import load_dataset
from sentence_transformers import SentenceTransformer, InputExample
from sentence_transformers.evaluation import EmbeddingSimilarityEvaluator

 
test_data = load_dataset('stsb_multi_mt', 'es', split='test')
test_data = test_data.rename_columns({'similarity_score': 'label'})
test_data = test_data.map(lambda x: {'label': x['label'] / 5.0})

samples = []
for sample in test_data:
    samples.append(InputExample(
        texts=[sample['sentence1'], sample['sentence2']],
        label=sample['label']
    ))
    
evaluator = EmbeddingSimilarityEvaluator.from_input_examples(
    samples, write_csv=False
)

model = SentenceTransformer('mrm8488/distiluse-base-multilingual-cased-v2-finetuned-stsb_multi_mt-es')

evaluator(model)

# It outputs: 0.7604056195656299
```

## Evaluation Results

 **Spearman’s rank correlation: 0.7604056195656299**

For an automated evaluation of this model, see the *Sentence Embeddings Benchmark*: [https://seb.sbert.net](https://seb.sbert.net?model_name={MODEL_NAME})


## Training
The model was trained with the parameters:

**DataLoader**:

`sentence_transformers.datasets.NoDuplicatesDataLoader.NoDuplicatesDataLoader` of length 906 with parameters:
```
{'batch_size': 16}
```

**Loss**:

`sentence_transformers.losses.MultipleNegativesRankingLoss.MultipleNegativesRankingLoss` with parameters:
  ```
  {'scale': 20.0, 'similarity_fct': 'cos_sim'}
  ```

Parameters of the fit()-Method:
```
{
    "epochs": 3,
    "evaluation_steps": 0,
    "evaluator": "NoneType",
    "max_grad_norm": 1,
    "optimizer_class": "<class 'transformers.optimization.AdamW'>",
    "optimizer_params": {
        "lr": 2e-05
    },
    "scheduler": "WarmupLinear",
    "steps_per_epoch": null,
    "warmup_steps": 271,
    "weight_decay": 0.01
}
```


## Full Model Architecture
```
SentenceTransformer(
  (0): Transformer({'max_seq_length': 512, 'do_lower_case': False}) with Transformer model: DistilBertModel 
  (1): Pooling({'word_embedding_dimension': 768, 'pooling_mode_cls_token': False, 'pooling_mode_mean_tokens': True, 'pooling_mode_max_tokens': False, 'pooling_mode_mean_sqrt_len_tokens': False})
)
```

## Citing & Authors

<!--- Describe where people can find more information -->