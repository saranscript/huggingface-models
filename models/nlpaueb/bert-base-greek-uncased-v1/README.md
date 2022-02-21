---
language: el
pipeline_tag: fill-mask
thumbnail: https://github.com/nlpaueb/GreekBERT/raw/master/greek-bert-logo.png
widget:
 - text: "Σήμερα είναι μια [MASK] μέρα."
---

# GreekBERT

A Greek version of BERT pre-trained language model.

<img src="https://github.com/nlpaueb/GreekBERT/raw/master/greek-bert-logo.png" width="600"/> 


## Pre-training corpora

The pre-training corpora of `bert-base-greek-uncased-v1` include:

* The Greek part of [Wikipedia](https://el.wikipedia.org/wiki/Βικιπαίδεια:Αντίγραφα_της_βάσης_δεδομένων),
* The Greek part of [European Parliament Proceedings Parallel Corpus](https://www.statmt.org/europarl/), and
* The Greek part of [OSCAR](https://traces1.inria.fr/oscar/), a cleansed version of [Common Crawl](https://commoncrawl.org).

Future release will also include:

* The entire corpus of Greek legislation, as published by the [National Publication Office](http://www.et.gr),  
* The entire corpus of EU legislation (Greek translation), as published in [Eur-Lex](https://eur-lex.europa.eu/homepage.html?locale=en).

## Pre-training details

* We trained BERT using the official code provided in Google BERT's GitHub repository (https://github.com/google-research/bert).* We then used [Hugging Face](https://huggingface.co)'s [Transformers](https://github.com/huggingface/transformers) conversion script to convert the TF checkpoint and vocabulary in the desired format in order to be able to load the model in two lines of code for both PyTorch and TF2 users.
* We released a model similar to the English `bert-base-uncased` model (12-layer, 768-hidden, 12-heads, 110M parameters).
* We chose to follow the same training set-up: 1 million training steps with batches of 256 sequences of length 512 with an initial learning rate 1e-4.
* We were able to use a single Google Cloud TPU v3-8 provided for free from [TensorFlow Research Cloud (TFRC)](https://www.tensorflow.org/tfrc), while also utilizing [GCP research credits](https://edu.google.com/programs/credits/research). Huge thanks to both Google programs for supporting us!

\* You can still have access to the original TensorFlow checkpoints from this [Google Drive folder](https://drive.google.com/drive/folders/1ZjlaE4nvdtgqXiVBTVHCF5I9Ff8ZmztE?usp=sharing).

## Requirements

We published `bert-base-greek-uncased-v1` as part of [Hugging Face](https://huggingface.co)'s [Transformers](https://github.com/huggingface/transformers) repository. So, you need to install the transformers library through pip along with PyTorch or Tensorflow 2.

```
pip install transformers
pip install (torch|tensorflow)
```

## Pre-process text (Deaccent - Lower)

**NOTICE:** Preprocessing is now natively supported by the default tokenizer. No need to include the following code.

In order to use `bert-base-greek-uncased-v1`, you have to pre-process texts to lowercase letters and remove all Greek diacritics.

```python

import unicodedata

def strip_accents_and_lowercase(s):
   return ''.join(c for c in unicodedata.normalize('NFD', s)
                  if unicodedata.category(c) != 'Mn').lower()

accented_string = "Αυτή είναι η Ελληνική έκδοση του BERT."
unaccented_string = strip_accents_and_lowercase(accented_string)

print(unaccented_string) # αυτη ειναι η ελληνικη εκδοση του bert.

```

## Load Pretrained Model 

```python
from transformers import AutoTokenizer, AutoModel

tokenizer = AutoTokenizer.from_pretrained("nlpaueb/bert-base-greek-uncased-v1")
model = AutoModel.from_pretrained("nlpaueb/bert-base-greek-uncased-v1")
```

## Use Pretrained Model as a Language Model

```python
import torch
from transformers import *

# Load model and tokenizer
tokenizer_greek = AutoTokenizer.from_pretrained('nlpaueb/bert-base-greek-uncased-v1')
lm_model_greek = AutoModelWithLMHead.from_pretrained('nlpaueb/bert-base-greek-uncased-v1')

# ================ EXAMPLE 1 ================
text_1 = 'O ποιητής έγραψε ένα [MASK] .'
# EN: 'The poet wrote a [MASK].'
input_ids = tokenizer_greek.encode(text_1)
print(tokenizer_greek.convert_ids_to_tokens(input_ids))
# ['[CLS]', 'o', 'ποιητης', 'εγραψε', 'ενα', '[MASK]', '.', '[SEP]']
outputs = lm_model_greek(torch.tensor([input_ids]))[0]
print(tokenizer_greek.convert_ids_to_tokens(outputs[0, 5].max(0)[1].item()))
# the most plausible prediction for [MASK] is "song"

# ================ EXAMPLE 2 ================
text_2 = 'Είναι ένας [MASK] άνθρωπος.'
# EN: 'He is a [MASK] person.'
input_ids = tokenizer_greek.encode(text_2)
print(tokenizer_greek.convert_ids_to_tokens(input_ids))
# ['[CLS]', 'ειναι', 'ενας', '[MASK]', 'ανθρωπος', '.', '[SEP]']
outputs = lm_model_greek(torch.tensor([input_ids]))[0]
print(tokenizer_greek.convert_ids_to_tokens(outputs[0, 3].max(0)[1].item()))
# the most plausible prediction for [MASK] is "good"

# ================ EXAMPLE 3 ================
text_3 = 'Είναι ένας [MASK] άνθρωπος και κάνει συχνά [MASK].'
# EN: 'He is a [MASK] person he does frequently [MASK].'
input_ids = tokenizer_greek.encode(text_3)
print(tokenizer_greek.convert_ids_to_tokens(input_ids))
# ['[CLS]', 'ειναι', 'ενας', '[MASK]', 'ανθρωπος', 'και', 'κανει', 'συχνα', '[MASK]', '.', '[SEP]']
outputs = lm_model_greek(torch.tensor([input_ids]))[0]
print(tokenizer_greek.convert_ids_to_tokens(outputs[0, 8].max(0)[1].item()))
# the most plausible prediction for the second [MASK] is "trips"
```

## Evaluation on downstream tasks

For detailed results read the article:

GREEK-BERT: The Greeks visiting Sesame Street. John Koutsikakis, Ilias Chalkidis, Prodromos Malakasiotis and Ion Androutsopoulos. In the Proceedings of the 11th Hellenic Conference on Artificial Intelligence (SETN 2020). Held Online. 2020. (https://arxiv.org/abs/2008.12014)


### Named Entity Recognition with Greek NER dataset

| Model name          | Micro F1                              |
| ------------------- | ------------------------------------  |
BILSTM-CNN-CRF (Ma and Hovy, 2016)  | 76.4 ± 2.07
M-BERT-UNCASED (Devlin et al., 2019) | 81.5 ± 1.77
M-BERT-CASED (Devlin et al., 2019)| 82.1 ± 1.35
XLM-R  (Conneau et al., 2020)| 84.8 ± 1.50
GREEK-BERT (ours)   | **85.7 ± 1.00**


### Natural Language Inference with XNLI

| Model name          | Accuracy                              |
| ------------------- | ------------------------------------  |
DAM (Parikh et al., 2016) | 68.5 ± 1.71
M-BERT-UNCASED (Devlin et al., 2019) | 73.9 ± 0.64
M-BERT-CASED (Devlin et al., 2019) | 73.5 ± 0.49
XLM-R (Conneau et al., 2020) | 77.3 ± 0.41
GREEK-BERT (ours)   | **78.6 ± 0.62**



## Author

The model has been officially released with the article "GREEK-BERT: The Greeks visiting Sesame Street. John Koutsikakis, Ilias Chalkidis, Prodromos Malakasiotis and Ion Androutsopoulos. In the Proceedings of the 11th Hellenic Conference on Artificial Intelligence (SETN 2020). Held Online. 2020" (https://arxiv.org/abs/2008.12014).

If you use the model, please cite the following:

```
@inproceedings{greek-bert,
author = {Koutsikakis, John and Chalkidis, Ilias and Malakasiotis, Prodromos and Androutsopoulos, Ion},
title = {GREEK-BERT: The Greeks Visiting Sesame Street},
year = {2020},
isbn = {9781450388788},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3411408.3411440},
booktitle = {11th Hellenic Conference on Artificial Intelligence},
pages = {110–117},
numpages = {8},
location = {Athens, Greece},
series = {SETN 2020}
}
```


Ilias Chalkidis on behalf of [AUEB's Natural Language Processing Group](http://nlp.cs.aueb.gr)

| Github: [@ilias.chalkidis](https://github.com/iliaschalkidis) | Twitter: [@KiddoThe2B](https://twitter.com/KiddoThe2B) |

## About Us

[AUEB's Natural Language Processing Group](http://nlp.cs.aueb.gr) develops algorithms, models, and systems that allow computers to process and generate natural language texts.

The group's current research interests include:
* question answering systems for databases, ontologies, document collections, and the Web, especially biomedical question answering,
* natural language generation from databases and ontologies, especially Semantic Web ontologies,
text classification, including filtering spam and abusive content,
* information extraction and opinion mining, including legal text analytics and sentiment analysis,
* natural language processing tools for Greek, for example parsers and named-entity recognizers,
machine learning in natural language processing, especially deep learning.

The group is part of the Information Processing Laboratory of the Department of Informatics of the Athens University of Economics and Business.
