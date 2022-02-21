---
language: ja
license: mit
datasets:
- mC4 Japanese
---

# transformers-ud-japanese-electra-ginza (sudachitra-wordpiece, mC4 Japanese) - [MIYAGINO](https://www.ntj.jac.go.jp/assets/images/member/pertopics/image/per100510_3.jpg)

This is an [ELECTRA](https://github.com/google-research/electra) model pretrained on approximately 200M Japanese sentences.

The input text is tokenized by [SudachiTra](https://github.com/WorksApplications/SudachiTra) with the WordPiece subword tokenizer.
See `tokenizer_config.json` for the setting details.

## How to use

```python
from transformers import ElectraModel
from sudachitra import ElectraSudachipyTokenizer
model = ElectraModel.from_pretrained("megagonlabs/transformers-ud-japanese-electra-base-discriminator")
tokenizer = ElectraSudachipyTokenizer.from_pretrained("megagonlabs/transformers-ud-japanese-electra-base-discriminator")
model(**tokenizer("まさにオールマイティーな商品だ。", return_tensors="pt")).last_hidden_state
tensor([[[-0.0498, -0.0285,  0.1042,  ...,  0.0062, -0.1253,  0.0338],
         [-0.0686,  0.0071,  0.0087,  ..., -0.0210, -0.1042, -0.0320],
         [-0.0636,  0.1465,  0.0263,  ...,  0.0309, -0.1841,  0.0182],
         ...,
         [-0.1500, -0.0368, -0.0816,  ..., -0.0303, -0.1653,  0.0650],
         [-0.0457,  0.0770, -0.0183,  ..., -0.0108, -0.1903,  0.0694],
         [-0.0981, -0.0387,  0.1009,  ..., -0.0150, -0.0702,  0.0455]]],
       grad_fn=<NativeLayerNormBackward>)
```

## Model architecture

The model architecture is the same as the original ELECTRA base model; 12 layers, 768 dimensions of hidden states, and 12 attention heads.

## Training data and libraries

This model is trained on the Japanese texts extracted from the [mC4](https://huggingface.co/datasets/mc4) Common Crawl's multilingual web crawl corpus.
We used the [Sudachi](https://github.com/WorksApplications/Sudachi) to split texts into sentences, and also applied a simple rule-based filter to remove nonlinguistic segments of mC4 multilingual corpus.
The extracted texts contains over 600M sentences in total, and we used approximately 200M sentences for pretraining.

We used [NVIDIA's TensorFlow2-based ELECTRA implementation](https://github.com/NVIDIA/DeepLearningExamples/tree/master/TensorFlow2/LanguageModeling/ELECTRA) for pretraining. The time required for the pretrainig was about 110 hours using GCP DGX A100 8gpu instance with enabling Automatic Mixed Precision.

## Licenses

The pretrained models are distributed under the terms of the [MIT License](https://opensource.org/licenses/mit-license.php).

## Citations

- mC4

Contains information from `mC4` which is made available under the [ODC Attribution License](https://opendatacommons.org/licenses/by/1-0/).
```
@article{2019t5,
    author = {Colin Raffel and Noam Shazeer and Adam Roberts and Katherine Lee and Sharan Narang and Michael Matena and Yanqi Zhou and Wei Li and Peter J. Liu},
    title = {Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer},
    journal = {arXiv e-prints},
    year = {2019},
    archivePrefix = {arXiv},
    eprint = {1910.10683},
}
```