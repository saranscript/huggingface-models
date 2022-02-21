---
language: 
  - en
tags:
- simcls
datasets:
- billsum
---


# SimCLS

SimCLS is a framework for abstractive summarization presented in [SimCLS: A Simple Framework for Contrastive Learning of Abstractive Summarization](https://arxiv.org/abs/2106.01890).
It is a two-stage approach consisting of a *generator* and a *scorer*. In the first stage, a large pre-trained model for abstractive summarization (the *generator*) is used to generate candidate summaries, whereas, in the second stage, the *scorer* assigns a score to each candidate given the source document. The final summary is the highest-scoring candidate.

This model is the *scorer* trained for summarization of BillSum ([paper](https://arxiv.org/abs/1910.00523), [datasets](https://huggingface.co/datasets/billsum)). It should be used in conjunction with [google/pegasus-billsum](https://huggingface.co/google/pegasus-billsum). See [our Github repository](https://github.com/andrejmiscic/simcls-pytorch) for details on training, evaluation, and usage.

## Usage

```bash
git clone https://github.com/andrejmiscic/simcls-pytorch.git
cd simcls-pytorch
pip3 install torch torchvision torchaudio transformers sentencepiece
```

```python
from src.model import SimCLS, GeneratorType

summarizer = SimCLS(generator_type=GeneratorType.Pegasus,
                    generator_path="google/pegasus-billsum",
                    scorer_path="andrejmiscic/simcls-scorer-billsum")

document = "This is a legal document."
summary = summarizer(document)
print(summary)
```

### Results

All of our results are reported together with 95% confidence intervals computed using 10000 iterations of bootstrap. See [SimCLS paper](https://arxiv.org/abs/2106.01890) for a description of baselines.
We believe the discrepancies of Rouge-L scores between the original Pegasus work and our evaluation are due to the computation of the metric. Namely, we use a summary level Rouge-L score.

| System          |               Rouge-1 |               Rouge-2 |              Rouge-L\* |
|-----------------|----------------------:|----------------------:|----------------------:|
| Pegasus         |                 57.31 |                 40.19 |                 45.82 |
| **Our results** |          ---          |          ---          |          ---          |
| Origin          | 56.24, [55.74, 56.74] | 37.46, [36.89, 38.03] | 50.71, [50.19, 51.22] |
| Min             | 44.37, [43.85, 44.89] | 25.75, [25.30, 26.22] | 38.68, [38.18, 39.16] |
| Max             | 62.88, [62.42, 63.33] | 43.96, [43.39, 44.54] | 57.50, [57.01, 58.00] |
| Random          | 54.93, [54.43, 55.43] | 35.42, [34.85, 35.97] | 49.19, [48.68, 49.70] |
| **SimCLS**      | 57.49, [57.01, 58.00] | 38.54, [37.98, 39.10] | 51.91, [51.39, 52.43] |

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
