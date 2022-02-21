# Nyströmformer

Nyströmformer model for masked language modeling (MLM) pretrained on BookCorpus and English Wikipedia for sequence length 512.

## About Nyströmformer

The Nyströmformer model was proposed in [Nyströmformer: A Nyström-Based Algorithm for Approximating Self-Attention](https://arxiv.org/abs/2102.03902) by Yunyang Xiong, Zhanpeng Zeng, Rudrasis Chakraborty, Mingxing Tan, Glenn Fung, Yin Li, and Vikas Singh.

The abstract from the paper is the following:

Transformers have emerged as a powerful tool for a broad range of natural language processing tasks. A key component that drives the impressive performance of Transformers is the self-attention mechanism that encodes the influence or dependence of other tokens on each specific token. While beneficial, the quadratic complexity of self-attention on the input sequence length has limited its application to longer sequences — a topic being actively studied in the community. To address this limitation, we propose Nyströmformer — a model that exhibits favorable scalability as a function of sequence length. Our idea is based on adapting the Nyström method to approximate standard self-attention with O(n) complexity. The scalability of Nyströmformer enables application to longer sequences with thousands of tokens. We perform evaluations on multiple downstream tasks on the GLUE benchmark and IMDB reviews with standard sequence length, and find that our Nyströmformer performs comparably, or in a few cases, even slightly better, than standard self-attention. On longer sequence tasks in the Long Range Arena (LRA) benchmark, Nyströmformer performs favorably relative to other efficient self-attention methods. Our code is available at this https URL.

## Usage

```python
>>> from transformers import pipeline
>>> unmasker = pipeline('fill-mask', model='uw-madison/nystromformer-512')
>>> unmasker("Paris is the [MASK] of France.")

[{'score': 0.829957902431488,
  'token': 1030,
  'token_str': 'capital',
  'sequence': 'paris is the capital of france.'},
 {'score': 0.022157637402415276,
  'token': 16081,
  'token_str': 'birthplace',
  'sequence': 'paris is the birthplace of france.'},
 {'score': 0.01904447190463543,
  'token': 197,
  'token_str': 'name',
  'sequence': 'paris is the name of france.'},
 {'score': 0.017583081498742104,
  'token': 1107,
  'token_str': 'kingdom',
  'sequence': 'paris is the kingdom of france.'},
 {'score': 0.005948934704065323,
  'token': 148,
  'token_str': 'city',
  'sequence': 'paris is the city of france.'}]
```