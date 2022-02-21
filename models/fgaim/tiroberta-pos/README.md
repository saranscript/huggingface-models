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
- name: tiroberta-base-pos
  results:
  - task:
      name: Token Classification
      type: token-classification
    metrics:
    - name: F1
      type: f1
      value: 0.9562
    - name: Precision
      type: precision
      value: 0.9562
    - name: Recall
      type: recall
      value: 0.9562
    - name: Accuracy
      type: accuracy
      value: 0.9562
---


# Tigrinya POS tagging with TiRoBERTa

This model is a fine-tuned version of [TiRoBERTa](https://huggingface.co/fgaim/tiroberta) on the NTC-v1 dataset (Tedla et al. 2016).

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
- Loss: 0.3194
- Adj Precision: 0.9219
- Adj Recall: 0.9335
- Adj F1: 0.9277
- Adj Number: 1670
- Adv Precision: 0.8297
- Adv Recall: 0.8554
- Adv F1: 0.8423
- Adv Number: 484
- Con Precision: 0.9844
- Con Recall: 0.9763
- Con F1: 0.9804
- Con Number: 972
- Fw Precision: 0.7895
- Fw Recall: 0.5357
- Fw F1: 0.6383
- Fw Number: 28
- Int Precision: 0.6552
- Int Recall: 0.7308
- Int F1: 0.6909
- Int Number: 26
- N Precision: 0.9650
- N Recall: 0.9662
- N F1: 0.9656
- N Number: 3992
- Num Precision: 0.9747
- Num Recall: 0.9665
- Num F1: 0.9706
- Num Number: 239
- N Prp Precision: 0.9308
- N Prp Recall: 0.9447
- N Prp F1: 0.9377
- N Prp Number: 470
- N V Precision: 0.9854
- N V Recall: 0.9736
- N V F1: 0.9794
- N V Number: 416
- Pre Precision: 0.9722
- Pre Recall: 0.9625
- Pre F1: 0.9673
- Pre Number: 907
- Pro Precision: 0.9448
- Pro Recall: 0.9236
- Pro F1: 0.9341
- Pro Number: 445
- Pun Precision: 1.0
- Pun Recall: 0.9994
- Pun F1: 0.9997
- Pun Number: 1607
- Unc Precision: 1.0
- Unc Recall: 0.875
- Unc F1: 0.9333
- Unc Number: 16
- V Precision: 0.8780
- V Recall: 0.9231
- V F1: 0.9
- V Number: 78
- V Aux Precision: 0.9685
- V Aux Recall: 0.9878
- V Aux F1: 0.9780
- V Aux Number: 654
- V Ger Precision: 0.9388
- V Ger Recall: 0.9571
- V Ger F1: 0.9479
- V Ger Number: 513
- V Imf Precision: 0.9634
- V Imf Recall: 0.9497
- V Imf F1: 0.9565
- V Imf Number: 914
- V Imv Precision: 0.8793
- V Imv Recall: 0.7286
- V Imv F1: 0.7969
- V Imv Number: 70
- V Prf Precision: 0.8960
- V Prf Recall: 0.9082
- V Prf F1: 0.9020
- V Prf Number: 294
- V Rel Precision: 0.9678
- V Rel Recall: 0.9538
- V Rel F1: 0.9607
- V Rel Number: 757
- Overall Precision: 0.9562
- Overall Recall: 0.9562
- Overall F1: 0.9562
- Overall Accuracy: 0.9562

### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3


## Citation

If you use this model in your product or research, please cite as follows:

```
@article{Fitsum2021TiPLMs,
  author={Fitsum Gaim and Wonsuk Yang and Jong C. Park},
  title={Monolingual Pre-trained Language Models for Tigrinya},
  year=2021,
  publisher={WiNLP 2021/EMNLP 2021}
}
```


## References

```
Tedla, Y., Yamamoto, K. & Marasinghe, A. 2016.
Tigrinya Part-of-Speech Tagging with Morphological Patterns and the New Nagaoka Tigrinya Corpus.
International Journal Of Computer Applications 146 pp. 33-41 (2016).
```
