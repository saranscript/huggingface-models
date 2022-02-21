---
language: de
tags: 
- exbert
- German
---

<a href="https://huggingface.co/exbert/?model=smanjil/German-MedBERT">
  <img width="300px" src="https://cdn-media.huggingface.co/exbert/button.png">
</a>

# German Medical BERT

This is a fine-tuned model on the Medical domain for the German language and based on German BERT. This model has only been trained to improve on-target tasks (Masked Language Model). It can later be used to perform a downstream task of your needs, while I performed it for the NTS-ICD-10 text classification task.

## Overview
**Language model:** bert-base-german-cased

**Language:** German

**Fine-tuning:** Medical articles (diseases, symptoms, therapies, etc..)

**Eval data:** NTS-ICD-10 dataset (Classification)

**Infrastructure:** Google Colab


## Details
- We fine-tuned using Pytorch with Huggingface library on Colab GPU.
- With standard parameter settings for fine-tuning as mentioned in the original BERT paper.
- Although had to train for up to 25 epochs for classification.

## Performance (Micro precision, recall, and f1 score for multilabel code classification)
|Models|P|R|F1|
|:------|:------|:------|:------|
|German BERT|86.04|75.82|80.60|
|German MedBERT-256 (fine-tuned)|87.41|77.97|82.42|
|German MedBERT-512 (fine-tuned)|87.75|78.26|82.73|


## Author
Manjil Shrestha: `shresthamanjil21 [at] gmail.com`

## Related Paper: [Report](https://opus4.kobv.de/opus4-rhein-waal/frontdoor/index/index/searchtype/collection/id/16225/start/0/rows/10/doctypefq/masterthesis/docId/740)

Get in touch:
[LinkedIn](https://www.linkedin.com/in/manjil-shrestha-038527b4/)
