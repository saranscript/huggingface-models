---
language:
  - en
pipeline_tag: sentence-similarity
tags:
  - sentence-transformers
  - feature-extraction
  - sentence-similarity
  - transformers
datasets:
  - anli
  - multi_nli
  - snli
---

# sbert-roberta-large-anli-mnli-snli

This is a [sentence-transformers](https://www.SBERT.net) model: It maps sentences & paragraphs to a 768 dimensional dense vector space and can be used for tasks like clustering or semantic search.

The model is weight initialized by RoBERTa-large and trained on ANLI (Nie et al., 2020), MNLI (Williams et al., 2018), and SNLI (Bowman et al., 2015) using the [`training_nli.py`](https://github.com/UKPLab/sentence-transformers/blob/v0.3.5/examples/training/nli/training_nli.py) example script.

Training Details:

- Learning rate: 2e-5
- Batch size: 8
- Pooling: Mean
- Training time: ~20 hours on one [NVIDIA GeForce RTX 2080 Ti](https://www.nvidia.com/en-us/geforce/graphics-cards/rtx-2080-ti/)

## Usage (Sentence-Transformers)

Using this model becomes easy when you have [sentence-transformers](https://www.SBERT.net) installed:

```bash
pip install -U sentence-transformers
```

Then you can use the model like this:

```python
from sentence_transformers import SentenceTransformer
sentences = ["This is an example sentence", "Each sentence is converted"]

model = SentenceTransformer("usc-isi/sbert-roberta-large-anli-mnli-snli")
embeddings = model.encode(sentences)
print(embeddings)
```

## Usage (Hugging Face Transformers)

Without [sentence-transformers](https://www.SBERT.net), you can use the model like this: first, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.

```python
import torch
from transformers import AutoModel, AutoTokenizer


# Mean Pooling - Take attention mask into account for correct averaging
def mean_pooling(model_output, attention_mask):
    token_embeddings = model_output[0]  # First element of model_output contains all token embeddings
    input_mask_expanded = attention_mask.unsqueeze(-1).expand(token_embeddings.size()).float()
    return torch.sum(token_embeddings * input_mask_expanded, 1) / torch.clamp(input_mask_expanded.sum(1), min=1e-9)


# Sentences we want sentence embeddings for
sentences = ["This is an example sentence", "Each sentence is converted"]

# Load model from HuggingFace Hub
tokenizer = AutoTokenizer.from_pretrained("usc-isi/sbert-roberta-large-anli-mnli-snli")
model = AutoModel.from_pretrained("usc-isi/sbert-roberta-large-anli-mnli-snli")

# Tokenize sentences
encoded_input = tokenizer(sentences, padding=True, truncation=True, return_tensors="pt")

# Compute token embeddings
with torch.no_grad():
    model_output = model(**encoded_input)

# Perform pooling. In this case, max pooling.
sentence_embeddings = mean_pooling(model_output, encoded_input["attention_mask"])

print("Sentence embeddings:")
print(sentence_embeddings)
```

## Evaluation Results

See section 4.1 of our paper for evaluation results.

## Full Model Architecture

```text
SentenceTransformer(
  (0): Transformer({'max_seq_length': 128, 'do_lower_case': False}) with Transformer model: RobertaModel
  (1): Pooling({'word_embedding_dimension': 768, 'pooling_mode_cls_token': False, 'pooling_mode_mean_tokens': True, 'pooling_mode_max_tokens': False, 'pooling_mode_mean_sqrt_len_tokens': False})
)
```

## Citing & Authors

For more information about the project, see our paper:

> Ciosici, Manuel, et al. "Machine-Assisted Script Curation." _Proceedings of the 2021 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies: Demonstrations_, Association for Computational Linguistics, 2021, pp. 8–17. _ACLWeb_, <https://www.aclweb.org/anthology/2021.naacl-demos.2>.

## References

- Samuel R. Bowman, Gabor Angeli, Christopher Potts, and Christopher D. Manning. 2015. [A large annotated corpus for learning natural language inference](https://doi.org/10.18653/v1/D15-1075). In _Proceedings of the 2015 Conference on Empirical Methods in Natural Language Processing_, pages 632–642, Lisbon, Portugal. Association for Computational Linguistics.
- Yixin Nie, Adina Williams, Emily Dinan, Mohit Bansal, Jason Weston, and Douwe Kiela. 2020. [AdversarialNLI: A new benchmark for natural language understanding](https://doi.org/10.18653/v1/2020.acl-main.441). In _Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics_, pages 4885–4901, Online. Association for Computational Linguistics.
- Adina Williams, Nikita Nangia, and Samuel Bowman. 2018. [A broad-coverage challenge corpus for sentence understanding through inference](https://doi.org/10.18653/v1/N18-1101). In _Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Volume 1 (Long Papers)_, pages 1112–1122, New Orleans, Louisiana. Association for Computational Linguistics.
