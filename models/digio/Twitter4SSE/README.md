---
language: 
  - en
pipeline_tag: sentence-similarity
tags:
- Pytorch
- Sentence Transformers
- Transformers
license: "apache-2.0"
---

# Twitter4SSE

This model maps texts to 768 dimensional dense embeddings that encode semantic similarity. 
It was trained with Multiple Negatives Ranking Loss (MNRL) on a Twitter dataset. 
It was initialized from [BERTweet](https://huggingface.co/vinai/bertweet-base) and trained with [Sentence-transformers](https://www.sbert.net/). 

## Usage

The model is easier to use with sentence-trainsformers library

```
pip install -U sentence-transformers
```

```
from sentence_transformers import SentenceTransformer
sentences = ["This is the first tweet", "This is the second tweet"]

model = SentenceTransformer('digio/Twitter4SSE')
embeddings = model.encode(sentences)
print(embeddings)
```


Without sentence-transfomer library, please refer to [this repository](https://huggingface.co/sentence-transformers) for detailed instructions on how to use Sentence Transformers on Huggingface. 

## Citing & Authors

The official paper [Exploiting Twitter as Source of Large Corpora of Weakly Similar Pairs for Semantic Sentence Embeddings](https://arxiv.org/abs/2110.02030) will be presented at EMNLP 2021. Further details will be available soon. 

```
@inproceedings{di-giovanni-brambilla-2021-exploiting,
    title = "Exploiting {T}witter as Source of Large Corpora of Weakly Similar Pairs for Semantic Sentence Embeddings",
    author = "Di Giovanni, Marco  and
      Brambilla, Marco",
    booktitle = "Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing",
    month = nov,
    year = "2021",
    address = "Online and Punta Cana, Dominican Republic",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.emnlp-main.780",
    pages = "9902--9910",
}
```

The official code is available on [GitHub](https://github.com/marco-digio/Twitter4SSE)


