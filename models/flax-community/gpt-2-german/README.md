---
language: 
- 
-
thumbnail: 
tags:
- 
-
- 
license: 
datasets:
- 
-
metrics:
- 
-
---

# GPT-2 GERMAN

## Model description

See [Open AI's model card](https://github.com/openai/gpt-2/blob/master/model_card.md) and [Huggingface's model card](https://huggingface.co/gpt2) for the original model.
## Intended uses & limitations

#### How to use

```python
def foo(bar)
  bar +=1
  return bar
```

#### Limitations and bias

On the Dangers of Stochastic Parrots: Can Language Models Be Too Big? ?? https://dl.acm.org/doi/10.1145/3442188.3445922

```
@inproceedings{10.1145/3442188.3445922,
author = {Bender, Emily M. and Gebru, Timnit and McMillan-Major, Angelina and Shmitchell, Shmargaret},
title = {On the Dangers of Stochastic Parrots: Can Language Models Be Too Big? ??},
year = {2021},
isbn = {9781450383097},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3442188.3445922},
doi = {10.1145/3442188.3445922},
abstract = {The past 3 years of work in NLP have been characterized by the development and deployment of ever larger language models, especially for English. BERT, its variants, GPT-2/3, and others, most recently Switch-C, have pushed the boundaries of the possible both through architectural innovations and through sheer size. Using these pretrained models and the methodology of fine-tuning them for specific tasks, researchers have extended the state of the art on a wide array of tasks as measured by leaderboards on specific benchmarks for English. In this paper, we take a step back and ask: How big is too big? What are the possible risks associated with this technology and what paths are available for mitigating those risks? We provide recommendations including weighing the environmental and financial costs first, investing resources into curating and carefully documenting datasets rather than ingesting everything on the web, carrying out pre-development exercises evaluating how the planned approach fits into research and development goals and supports stakeholder values, and encouraging research directions beyond ever larger language models.},
booktitle = {Proceedings of the 2021 ACM Conference on Fairness, Accountability, and Transparency},
pages = {610?623},
numpages = {14},
location = {Virtual Event, Canada},
series = {FAccT '21}
}
```

## Training data

https://huggingface.co/datasets/german-nlp-group/german_common_crawl

```json
{'url': 'http://my-shop.ru/shop/books/545473.html', 
'date_download': '2016-10-20T19:38:58Z',
 'digest': 'sha1:F62EMGYLZDIKF4UL5JZYU47KWGGUBT7T', 
 'length': 1155, 
 'nlines': 4, 
 'source_domain': 'my-shop.ru', 
 'title': 'Grammatikalische Liebeslieder. Methodische Vorschläge', 
 'raw_content': 'Grammatikalische Liebeslieder. [....]', 
 'cc_segment': 'crawl-data/CC-MAIN-2016-44/segments/1476988717783.68/wet/CC-MAIN-20161020183837-00354-ip-10-171-6-4.ec2.internal.warc.wet.gz', 
 'original_nlines': 99, 
 'original_length': 2672, 
 'language': 'de', 
 'language_score': 1.0, 
 'perplexity': 283.0, 
 'bucket': 'head'}"
 ```

## Training procedure

TODO (See [training](training.md))

## Eval results

TODO: Self-BLEU, Diversity, and other metrics from https://arxiv.org/abs/1904.09751
```
@inproceedings{DBLP:conf/iclr/HoltzmanBDFC20,
  author    = {Ari Holtzman and
               Jan Buys and
               Li Du and
               Maxwell Forbes and
               Yejin Choi},
  title     = {The Curious Case of Neural Text Degeneration},
  booktitle = {8th International Conference on Learning Representations, {ICLR} 2020,
               Addis Ababa, Ethiopia, April 26-30, 2020},
  publisher = {OpenReview.net},
  year      = {2020},
  url       = {https://openreview.net/forum?id=rygGQyrFvH},
  timestamp = {Thu, 21 Jan 2021 17:36:46 +0100},
  biburl    = {https://dblp.org/rec/conf/iclr/HoltzmanBDFC20.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
### BibTeX entry and citation info

Does the Huggingface hub generate DOIs? Otherwise maybe Kaggle or Zenodo to generate one.

```bibtex
@inproceedings{...,
  year={2021}
}
```
