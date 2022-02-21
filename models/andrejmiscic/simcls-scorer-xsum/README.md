---
language: 
  - en
tags:
- simcls
datasets:
- xsum
---

# SimCLS
SimCLS is a framework for abstractive summarization presented in [SimCLS: A Simple Framework for Contrastive Learning of Abstractive Summarization](https://arxiv.org/abs/2106.01890).
It is a two-stage approach consisting of a *generator* and a *scorer*. In the first stage, a large pre-trained model for abstractive summarization (the *generator*) is used to generate candidate summaries, whereas, in the second stage, the *scorer* assigns a score to each candidate given the source document. The final summary is the highest-scoring candidate.

This model is the *scorer* trained for summarization of XSum ([paper](https://arxiv.org/abs/1808.08745), [datasets](https://huggingface.co/datasets/xsum)). It should be used in conjunction with [google/pegasus-xsum](https://huggingface.co/google/pegasus-xsum). See [our Github repository](https://github.com/andrejmiscic/simcls-pytorch) for details on training, evaluation, and usage.

## Usage

```bash
git clone https://github.com/andrejmiscic/simcls-pytorch.git
cd simcls-pytorch
pip3 install torch torchvision torchaudio transformers sentencepiece
```

```python
from src.model import SimCLS, GeneratorType

summarizer = SimCLS(generator_type=GeneratorType.Pegasus,
                    generator_path="google/pegasus-xsum",
                    scorer_path="andrejmiscic/simcls-scorer-xsum")

article = "This is a news article."
summary = summarizer(article)
print(summary)
```

### Results

All of our results are reported together with 95% confidence intervals computed using 10000 iterations of bootstrap. See [SimCLS paper](https://arxiv.org/abs/2106.01890) for a description of baselines.

| System           |               Rouge-1 |               Rouge-2 |               Rouge-L |
|------------------|----------------------:|----------------------:|----------------------:|
| Pegasus          |                 47.21 |                 24.56 |                 39.25 |
| **SimCLS paper** |          ---          |          ---          |          ---          |
| Origin           |                 47.10 |                 24.53 |                 39.23 |
| Min              |                 40.97 |                 19.18 |                 33.68 |
| Max              |                 52.45 |                 28.28 |                 43.36 |
| Random           |                 46.72 |                 23.64 |                 38.55 |
| **SimCLS**       |                 47.61 |                 24.57 |                 39.44 |
|  **Our results** |          ---          |          ---          |          ---          |
| Origin           | 47.16, [46.85, 47.48] | 24.59, [24.25, 24.92] | 39.30, [38.96, 39.62] |
| Min              | 41.06, [40.76, 41.34] | 18.30, [18.03, 18.56] | 32.70, [32.42, 32.97] |
| Max              | 51.83, [51.53, 52.14] | 28.92, [28.57, 29.26] | 44.02, [43.69, 44.36] |
| Random           | 46.47, [46.17, 46.78] | 23.45, [23.13, 23.77] | 38.28, [37.96, 38.60] |
| **SimCLS**       | 47.17, [46.87, 47.46] | 23.90, [23.59, 24.23] | 38.96, [38.64, 39.29] |

### Citation of the original work

```bibtex
@inproceedings{liu-liu-2021-simcls,
    title = "{S}im{CLS}: A Simple Framework for Contrastive Learning of Abstractive Summarization",
    author = "Liu, Yixin  and
      Liu, Pengfei",
    booktitle = "Proceedings of the 59th Annual Meeting of the Association for Computational Linguistics and the 11th International Joint Conference on Natural Language Processing (Volume 2: Short Papers)",
    month = aug,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.acl-short.135",
    doi = "10.18653/v1/2021.acl-short.135",
    pages = "1065--1072",
}
```
