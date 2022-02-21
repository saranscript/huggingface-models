---
language: 
  - en
tags:
- simcls
datasets:
- cnn_dailymail
---

# SimCLS

SimCLS is a framework for abstractive summarization presented in [SimCLS: A Simple Framework for Contrastive Learning of Abstractive Summarization](https://arxiv.org/abs/2106.01890).
It is a two-stage approach consisting of a *generator* and a *scorer*. In the first stage, a large pre-trained model for abstractive summarization (the *generator*) is used to generate candidate summaries, whereas, in the second stage, the *scorer* assigns a score to each candidate given the source document. The final summary is the highest-scoring candidate.

This model is the *scorer* trained for summarization of CNN/DailyMail ([paper](https://arxiv.org/abs/1602.06023), [datasets](https://huggingface.co/datasets/cnn_dailymail)). It should be used in conjunction with [facebook/bart-large-cnn](https://huggingface.co/facebook/bart-large-cnn). See [our Github repository](https://github.com/andrejmiscic/simcls-pytorch) for details on training, evaluation, and usage.

## Usage

```bash
git clone https://github.com/andrejmiscic/simcls-pytorch.git
cd simcls-pytorch
pip3 install torch torchvision torchaudio transformers sentencepiece
```

```python
from src.model import SimCLS, GeneratorType

summarizer = SimCLS(generator_type=GeneratorType.Bart,
                    generator_path="facebook/bart-large-cnn",
                    scorer_path="andrejmiscic/simcls-scorer-cnndm")

article = "This is a news article."
summary = summarizer(article)
print(summary)
```

### Results

All of our results are reported together with 95% confidence intervals computed using 10000 iterations of bootstrap. See [SimCLS paper](https://arxiv.org/abs/2106.01890) for a description of baselines.

| System           |               Rouge-1 |               Rouge-2 |               Rouge-L |
|------------------|----------------------:|----------------------:|----------------------:|
| BART             |                 44.16 |                 21.28 |                 40.90 |
| **SimCLS paper** |          ---          |          ---          |          ---          |
| Origin           |                 44.39 |                 21.21 |                 41.28 |
| Min              |                 33.17 |                 11.67 |                 30.77 |
| Max              |                 54.36 |                 28.73 |                 50.77 |
| Random           |                 43.98 |                 20.06 |                 40.94 |
| **SimCLS**       |                 46.67 |                 22.15 |                 43.54 |
|  **Our results** |          ---          |          ---          |          ---          |
| Origin           | 44.41, [44.18, 44.63] | 21.05, [20.80, 21.29] | 41.53, [41.30, 41.75] |
| Min              | 33.43, [33.25, 33.62] | 10.97, [10.82, 11.12] | 30.57, [30.40, 30.74] |
| Max              | 53.87, [53.67, 54.08] | 29.72, [29.47, 29.98] | 51.13, [50.92, 51.34] |
| Random           | 43.94, [43.73, 44.16] | 20.09, [19.86, 20.31] | 41.06, [40.85, 41.27] |
| **SimCLS**       | 46.53, [46.32, 46.75] | 22.14, [21.91, 22.37] | 43.56, [43.34, 43.78] |

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
