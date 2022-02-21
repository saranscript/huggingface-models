# TUNiB-Electra
  
We release several new versions of the [ELECTRA](https://arxiv.org/abs/2003.10555) model, which we name TUNiB-Electra. There are two motivations. First, all the existing pre-trained Korean encoder models are monolingual, that is, they have knowledge about Korean only. Our bilingual models are based on the balanced corpora of Korean and English. Second, we want new off-the-shelf models trained on much more texts. To this end, we collected a large amount of Korean text from various sources such as blog posts, comments, news, web novels, etc., which sum up to 100 GB in total.


## How to use
  
You can use this model directly with [transformers](https://github.com/huggingface/transformers) library:
  
```python
from transformers import AutoModel, AutoTokenizer

# Small Model (Korean-only model)
tokenizer = AutoTokenizer.from_pretrained('tunib/electra-ko-small')
model = AutoModel.from_pretrained('tunib/electra-ko-small')
```

### Tokenizer example

```python
>>> from transformers import AutoTokenizer
>>> tokenizer = AutoTokenizer.from_pretrained('tunib/electra-ko-small')
>>> tokenizer.tokenize("tunib is a natural language processing tech startup.")
['tun', '##ib', 'is', 'a', 'natural', 'language', 'processing', 'tech', 'startup', '.']
>>> tokenizer.tokenize("튜닙은 자연어처리 테크 스타트업입니다.")
['튜', '##닙', '##은', '자연', '##어', '##처리', '테크', '스타트업', '##입니다', '.']
```
  
## Results on Korean downstream tasks
  
  
|                       |**# Params** |**Avg.**| **NSMC**<br/>(acc) | **Naver NER**<br/>(F1) | **PAWS**<br/>(acc) | **KorNLI**<br/>(acc) | **KorSTS**<br/>(spearman) | **Question Pair**<br/>(acc) | **KorQuaD (Dev)**<br/>(EM/F1) |**Korean-Hate-Speech (Dev)**<br/>(F1)| 
|  :----------------:| :----------------: | :--------------------: | :----------------: | :------------------: | :-----------------------: | :-------------------------: | :---------------------------: | :---------------------------: | :---------------------------: | :----------------: |
|***TUNiB-Electra-ko-small*** |   14M |  81.29|  **89.56**      |        84.98         |     72.85   |   77.08   |    78.76   | **94.98**  | 61.17 / 87.64  |  **64.50** |
|***TUNiB-Electra-ko-en-small*** |  18M |   81.44 | 89.28   |      85.15         |  75.75       | 77.06     | 77.61 | 93.79  | 80.55 / 89.77      |63.13 |
| [KoELECTRA-small-v3](https://github.com/monologg/KoELECTRA)    | 14M |  **82.58** | 89.36   |      **85.40**	     |    **77.45**    |    **78.60**    |       **80.79**      |     94.85    | **82.11 / 91.13**	|  63.07 | 
