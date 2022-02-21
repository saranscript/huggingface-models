---
language: 
- bn
licenses:
- cc-by-nc-sa-4.0
---

# BanglaBERT

This repository contains the pretrained discriminator checkpoint of the model **BanglaBERT**. This is an [ELECTRA](https://openreview.net/pdf?id=r1xMH1BtvB) discriminator model pretrained with the Replaced Token Detection (RTD) objective. Finetuned models using this checkpoint achieve state-of-the-art results on many of the NLP tasks in bengali. 

For finetuning on different downstream tasks such as `Sentiment classification`, `Named Entity Recognition`, `Natural Language Inference` etc., refer to the scripts in the official GitHub [repository](https://github.com/csebuetnlp/banglabert).

**Note**: This model was pretrained using a specific normalization pipeline available [here](https://github.com/csebuetnlp/normalizer). All finetuning scripts in the official GitHub repository uses this normalization by default. If you need to adapt the pretrained model for a different task make sure the text units are normalized using this pipeline before tokenizing to get best results. A basic example is given below:

## Using this model as a discriminator in `transformers` (tested on 4.11.0.dev0)

```python
from transformers import AutoModelForPreTraining, AutoTokenizer
from normalizer import normalize # pip install git+https://github.com/csebuetnlp/normalizer
import torch

model = AutoModelForPreTraining.from_pretrained("csebuetnlp/banglabert")
tokenizer = AutoTokenizer.from_pretrained("csebuetnlp/banglabert")

original_sentence = "আমি কৃতজ্ঞ কারণ আপনি আমার জন্য অনেক কিছু করেছেন।"
fake_sentence = "আমি হতাশ কারণ আপনি আমার জন্য অনেক কিছু করেছেন।"
fake_sentence = normalize(fake_sentence) # this normalization step is required before tokenizing the text

fake_tokens = tokenizer.tokenize(fake_sentence)
fake_inputs = tokenizer.encode(fake_sentence, return_tensors="pt")
discriminator_outputs = model(fake_inputs).logits
predictions = torch.round((torch.sign(discriminator_outputs) + 1) / 2)

[print("%7s" % token, end="") for token in fake_tokens]
print("\n" + "-" * 50)
[print("%7s" % int(prediction), end="") for prediction in predictions.squeeze().tolist()[1:-1]]
print("\n" + "-" * 50)
```

## Benchmarks
 
|             |   SC   |  EC   |  DC   |  NER     | NLI      |
|-------------|--------|-------|-------|----------|----------|
|`Metrics`      |   `Accuracy` | `F1*`  | `Accuracy` | `F1 (Entity)*`  | `Accuracy` |  
|[mBERT](https://huggingface.co/bert-base-multilingual-cased)        | 83.39  | 56.02 | 98.64 | 67.40    |  75.40   |
|[XLM-R](https://huggingface.co/xlm-roberta-base)        | 89.49  | 66.70 | 98.71 | 70.63    |   76.87  |    
|[sagorsarker/bangla-bert-base](https://huggingface.co/sagorsarker/bangla-bert-base) |  87.30  |  61.51  |  98.79   |  70.97   |   70.48     |
[monsoon-nlp/bangla-electra](https://huggingface.co/monsoon-nlp/bangla-electra)  |  73.54  | 34.55  | 97.64     | 52.57   |   63.48   |
|***BanglaBERT***   | **92.18** | **74.27** | **99.07** | **72.18** | **82.94**|

`*` - Weighted Average

The benchmarking datasets are as follows:
* **SC:** **[Sentiment Classification](https://ieeexplore.ieee.org/document/8554396/)**
* **EC:** **[Emotion Classification](https://aclanthology.org/2021.naacl-srw.19/)**
* **DC:** **[Document Classification](https://arxiv.org/abs/2005.00085)**
* **NER:** **[Named Entity Recognition](https://content.iospress.com/articles/journal-of-intelligent-and-fuzzy-systems/ifs179349)**
* **NLI:** **[Natural Language Inference](#datasets)**


## Citation

If you use this model, please cite the following paper:
```
@article{bhattacharjee2021banglabert,
  author    = {Abhik Bhattacharjee and Tahmid Hasan and Kazi Samin and Md Saiful Islam and M. Sohel Rahman and Anindya Iqbal and Rifat Shahriyar},
  title     = {BanglaBERT: Combating Embedding Barrier in Multilingual Models for Low-Resource Language Understanding},
  journal   = {CoRR},
  volume    = {abs/2101.00204},
  year      = {2021},
  url       = {https://arxiv.org/abs/2101.00204},
  eprinttype = {arXiv},
  eprint    = {2101.00204}
}
```

If you use the normalization module, please cite the following paper:
```
@inproceedings{hasan-etal-2020-low,
    title = "Not Low-Resource Anymore: Aligner Ensembling, Batch Filtering, and New Datasets for {B}engali-{E}nglish Machine Translation",
    author = "Hasan, Tahmid  and
      Bhattacharjee, Abhik  and
      Samin, Kazi  and
      Hasan, Masum  and
      Basak, Madhusudan  and
      Rahman, M. Sohel  and
      Shahriyar, Rifat",
    booktitle = "Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP)",
    month = nov,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.emnlp-main.207",
    doi = "10.18653/v1/2020.emnlp-main.207",
    pages = "2612--2623",
    abstract = "Despite being the seventh most widely spoken language in the world, Bengali has received much less attention in machine translation literature due to being low in resources. Most publicly available parallel corpora for Bengali are not large enough; and have rather poor quality, mostly because of incorrect sentence alignments resulting from erroneous sentence segmentation, and also because of a high volume of noise present in them. In this work, we build a customized sentence segmenter for Bengali and propose two novel methods for parallel corpus creation on low-resource setups: aligner ensembling and batch filtering. With the segmenter and the two methods combined, we compile a high-quality Bengali-English parallel corpus comprising of 2.75 million sentence pairs, more than 2 million of which were not available before. Training on neural models, we achieve an improvement of more than 9 BLEU score over previous approaches to Bengali-English machine translation. We also evaluate on a new test set of 1000 pairs made with extensive quality control. We release the segmenter, parallel corpus, and the evaluation set, thus elevating Bengali from its low-resource status. To the best of our knowledge, this is the first ever large scale study on Bengali-English machine translation. We believe our study will pave the way for future research on Bengali-English machine translation as well as other low-resource languages. Our data and code are available at https://github.com/csebuetnlp/banglanmt.",
}
```


