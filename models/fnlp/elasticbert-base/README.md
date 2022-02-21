# ElasticBERT-BASE

## Model description

This is an implementation of the `base` version of ElasticBERT.

[**Towards Efficient NLP: A Standard Evaluation and A Strong Baseline**](https://arxiv.org/pdf/2110.07038.pdf)

Xiangyang Liu, Tianxiang Sun, Junliang He, Lingling Wu, Xinyu Zhang, Hao Jiang, Zhao Cao, Xuanjing Huang, Xipeng Qiu

## Code link

[**fastnlp/elasticbert**](https://github.com/fastnlp/ElasticBERT)

## Usage

```python
>>> from transformers import BertTokenizer as ElasticBertTokenizer
>>> from models.configuration_elasticbert import ElasticBertConfig
>>> from models.modeling_elasticbert import ElasticBertForSequenceClassification

>>> num_output_layers = 1
>>> config = ElasticBertConfig.from_pretrained('fnlp/elasticbert-base', num_output_layers=num_output_layers )
>>> tokenizer = ElasticBertTokenizer.from_pretrained('fnlp/elasticbert-base')
>>> model = ElasticBertForSequenceClassification.from_pretrained('fnlp/elasticbert-base', config=config)

>>> input_ids = tokenizer.encode('The actors are fantastic .', return_tensors='pt')
>>> outputs = model(input_ids)
```

## Citation

```bibtex
@article{liu2021elasticbert,
  author    = {Xiangyang Liu and
               Tianxiang Sun and
               Junliang He and
               Lingling Wu and
               Xinyu Zhang and
               Hao Jiang and
               Zhao Cao and
               Xuanjing Huang and
               Xipeng Qiu},
  title     = {Towards Efficient {NLP:} {A} Standard Evaluation and {A} Strong Baseline},
  journal   = {CoRR},
  volume    = {abs/2110.07038},
  year      = {2021},
  url       = {https://arxiv.org/abs/2110.07038},
  eprinttype = {arXiv},
  eprint    = {2110.07038},
  timestamp = {Fri, 22 Oct 2021 13:33:09 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2110-07038.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```