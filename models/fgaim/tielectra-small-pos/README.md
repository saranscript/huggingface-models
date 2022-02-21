---
language: ti
widget:
- text: "ድምጻዊ ኣብርሃም ኣፈወርቂ ንዘልኣለም ህያው ኮይኑ ኣብ ልብና ይነብር"
datasets:
- TLMD
- NTC
metrics:
- f1
- precision
- recall
- accuracy
model-index:
- name: tielectra-small-pos
  results:
  - task:
      name: Token Classification
      type: token-classification
    metrics:
    - name: F1
      type: f1
      value: 0.9456
    - name: Precision
      type: precision
      value: 0.9456
    - name: Recall
      type: recall
      value: 0.9456
    - name: Accuracy
      type: accuracy
      value: 0.9456
---


# Tigrinya POS tagging with TiELECTRA

This model is a fine-tuned version of [TiELECTRA](https://huggingface.co/fgaim/tielectra-small) on the NTC-v1 dataset (Tedla et al. 2016).


## Basic usage

```python
from transformers import pipeline

ti_pos = pipeline("token-classification", model="fgaim/tielectra-small-pos")
ti_pos("ድምጻዊ ኣብርሃም ኣፈወርቂ ንዘልኣለም ህያው ኮይኑ ኣብ ልብና ይነብር")
```


## Training

### Hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0

### Results

The model achieves the following results on the test set:
- Loss: 0.2236
- Adj Precision: 0.9148
- Adj Recall: 0.9192
- Adj F1: 0.9170
- Adj Number: 1670
- Adv Precision: 0.8228
- Adv Recall: 0.8058
- Adv F1: 0.8142
- Adv Number: 484
- Con Precision: 0.9793
- Con Recall: 0.9743
- Con F1: 0.9768
- Con Number: 972
- Fw Precision: 0.5
- Fw Recall: 0.3214
- Fw F1: 0.3913
- Fw Number: 28
- Int Precision: 0.64
- Int Recall: 0.6154
- Int F1: 0.6275
- Int Number: 26
- N Precision: 0.9525
- N Recall: 0.9587
- N F1: 0.9556
- N Number: 3992
- Num Precision: 0.9825
- Num Recall: 0.9372
- Num F1: 0.9593
- Num Number: 239
- N Prp Precision: 0.9132
- N Prp Recall: 0.9404
- N Prp F1: 0.9266
- N Prp Number: 470
- N V Precision: 0.9667
- N V Recall: 0.9760
- N V F1: 0.9713
- N V Number: 416
- Pre Precision: 0.9645
- Pre Recall: 0.9592
- Pre F1: 0.9619
- Pre Number: 907
- Pro Precision: 0.9395
- Pro Recall: 0.9079
- Pro F1: 0.9234
- Pro Number: 445
- Pun Precision: 1.0
- Pun Recall: 0.9994
- Pun F1: 0.9997
- Pun Number: 1607
- Unc Precision: 0.9286
- Unc Recall: 0.8125
- Unc F1: 0.8667
- Unc Number: 16
- V Precision: 0.7609
- V Recall: 0.8974
- V F1: 0.8235
- V Number: 78
- V Aux Precision: 0.9581
- V Aux Recall: 0.9786
- V Aux F1: 0.9682
- V Aux Number: 654
- V Ger Precision: 0.9183
- V Ger Recall: 0.9415
- V Ger F1: 0.9297
- V Ger Number: 513
- V Imf Precision: 0.9473
- V Imf Recall: 0.9442
- V Imf F1: 0.9458
- V Imf Number: 914
- V Imv Precision: 0.8163
- V Imv Recall: 0.5714
- V Imv F1: 0.6723
- V Imv Number: 70
- V Prf Precision: 0.8927
- V Prf Recall: 0.8776
- V Prf F1: 0.8851
- V Prf Number: 294
- V Rel Precision: 0.9535
- V Rel Recall: 0.9485
- V Rel F1: 0.9510
- V Rel Number: 757
- Overall Precision: 0.9456
- Overall Recall: 0.9456
- Overall F1: 0.9456
- Overall Accuracy: 0.9456

### Framework versions

- Transformers 4.10.3
- Pytorch 1.9.0+cu111
- Datasets 1.10.2
- Tokenizers 0.10.1


## Citation

If you use this model in your product or research, please cite as follows:

```
@article{Fitsum2021TiPLMs,
  author= {Fitsum Gaim and Wonsuk Yang and Jong C. Park},
  title= {Monolingual Pre-trained Language Models for Tigrinya},
  year= 2021,
  publisher= {WiNLP 2021/EMNLP 2021}
}
```


## References

```
Tedla, Y., Yamamoto, K. & Marasinghe, A. 2016.
Tigrinya Part-of-Speech Tagging with Morphological Patterns and the New Nagaoka Tigrinya Corpus.
International Journal Of Computer Applications 146 pp. 33-41 (2016).
```
