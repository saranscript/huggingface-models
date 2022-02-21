---
language: el
license: gpl-3.0
tags:
- generated_from_trainer
- roberta
- Greek
- news
- transformers
model-index:
- name: roberta-el-news
  results: []
widget:
 - text: "Η κυβέρνηση μουδιασμένη από τη <mask> της έκθεσης Τσιόδρα-Λύτρα, επιχειρεί χωρίς να απαντά ουσιαστικά να ρίξει ευθύνες στον ΣΥΡΙΖΑ, που κυβερνούσε πριν... 2 χρόνια."
---

# RoBERTa Greek base model

Pretrained model on Greek language with the Masked Language Modeling (MLM) objective using [Hugging Face's](https://huggingface.co/) [Transformers](https://github.com/huggingface/transformers) library. This model is *NOT* case-sensitive and all Greek diacritics retained.

### How to use

You can use this model directly with a pipeline for masked language modeling:

```python
# example url 
# https://www.news247.gr/politiki/misologa-maximoy-gia-tin-ekthesi-tsiodra-lytra-gia-ti-thnitotita-ektos-meth.9462425.html 
# not present in train/eval set
from transformers import pipeline
pipe = pipeline('fill-mask', model='cvcio/roberta-el-news')
pipe(
    'Η κυβέρνηση μουδιασμένη από τη <mask> της έκθεσης Τσιόδρα-Λύτρα, '
    'επιχειρεί χωρίς να απαντά ουσιαστικά να ρίξει ευθύνες στον ΣΥΡΙΖΑ, που κυβερνούσε πριν... 2 χρόνια.'
)
# outputs
[
    {
        'sequence': 'Η κυβέρνηση μουδιασμένη από τη δημοσιοποίηση της έκθεσης Τσιόδρα-Λύτρα, επιχειρεί χωρίς να απαντά ουσιαστικά να ρίξει ευθύνες στον ΣΥΡΙΖΑ, που κυβερνούσε πριν... 2 χρόνια.', 
        'score': 0.5881184339523315, 'token': 20235, 'token_str': ' δημοσιοποίηση'
    }, 
    {
        'sequence': 'Η κυβέρνηση μουδιασμένη από τη δημοσίευση της έκθεσης Τσιόδρα-Λύτρα, επιχειρεί χωρίς να απαντά ουσιαστικά να ρίξει ευθύνες στον ΣΥΡΙΖΑ, που κυβερνούσε πριν... 2 χρόνια.', 
        'score': 0.05952141433954239, 'token': 9696, 'token_str': ' δημοσίευση'
    }, 
    {
        'sequence': 'Η κυβέρνηση μουδιασμένη από τη διαχείριση της έκθεσης Τσιόδρα-Λύτρα, επιχειρεί χωρίς να απαντά ουσιαστικά να ρίξει ευθύνες στον ΣΥΡΙΖΑ, που κυβερνούσε πριν... 2 χρόνια.', 
        'score': 0.029887061566114426, 'token': 4315, 'token_str': ' διαχείριση'
    }, 
    {
        'sequence': 'Η κυβέρνηση μουδιασμένη από τη διαρροή της έκθεσης Τσιόδρα-Λύτρα, επιχειρεί χωρίς να απαντά ουσιαστικά να ρίξει ευθύνες στον ΣΥΡΙΖΑ, που κυβερνούσε πριν... 2 χρόνια.', 
        'score': 0.022848669439554214, 'token': 24940, 'token_str': ' διαρροή'
    }, 
    {
        'sequence': 'Η κυβέρνηση μουδιασμένη από τη ματαίωση της έκθεσης Τσιόδρα-Λύτρα, επιχειρεί χωρίς να απαντά ουσιαστικά να ρίξει ευθύνες στον ΣΥΡΙΖΑ, που κυβερνούσε πριν... 2 χρόνια.', 
        'score': 0.01729060709476471, 'token': 46913, 'token_str': ' ματαίωση'
    }
]
```

## Training data

The model was pretrained on 8 millon unique news articles (~ approx 160M sentences, 33GB of text), collected with [MediaWatch](https://mediawatch.io/), from October 2016 upto December 2021.

## Preprocessing

The texts are tokenized using a byte version of Byte-Pair Encoding (BPE) and a vocabulary size of 50,265. During the preprocessing we only unescaped html text to the correspoing Unicode characters (ex. `&amp;` => `&`).

## Pretraining

The model was pretrained using an NVIDIA A10 GPU for 3 epochs (~ approx 760K steps, 182 hours) with a batch size of 14 (x2 gradient accumulation steps = 28) and a sequence length of 512 tokens. The optimizer used is Adam with a learning rate of 5e-5, and linear decay of the learning rate.

### Training results

| epochs | steps   | train/train_loss | train/loss  | eval/loss |
|-------:|--------:|-----------------:|------------:|----------:|
| 3.00   | 765,414 | 0.396            | 1.2356      | 0.9028    |

### Evaluation results

The model fine-tuned on ner task using the [elNER](https://github.com/nmpartzio/elner) dataset and achieved the following results:

| task | epochs | lr   | batch | dataset | precision | recall  | f1      | accuracy  |
|-----:|-------:|-----:|------:|--------:|----------:|--------:|--------:|----------:|
| ner  | 5.0    | 1e-5 | 16/16 | elNER4  | 0.8954    | 0.9280  | 0.9114  | 0.9872    |
| ner  | 5.0    | 1e-5 | 16/16 | elNER18 | 0.8874    | 0.9185  | 0.9027  | 0.9808    |

### Training hyperparameters

The following hyperparameters were used during training:

- learning_rate: 5e-5
- train_batch_size: 14
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 28
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Framework versions

- Transformers 4.13.0
- Pytorch 1.9.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3

## Authors

Dimitris Papaevagelou - [@andefined](https://github.com/andefined)

## About Us

[Civic Information Office](https://cvcio.org/) is a Non Profit Organization based in Athens, Greece focusing on creating technology and research products for the public interest.