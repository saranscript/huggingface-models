---
language:
- en
tags:
- legal
license: apache-2.0
metrics:
- precision
- recall
---





# LEGAL-ROBERTA
We introduce LEGAL-ROBERTA, which is a domain-specific language representation model fine-tuned on large-scale legal corpora(4.6 GB). 

## Demo



'This \<mask\> Agreement is between General Motors and John Murray .'



| Model        | top1 | top2    |  top3   | top4    | top5 |
| ------------ | ---- | --- | --- | --- | -------- |
| Bert         |  new    |   current  | proposed    |  marketing   |    joint      |
| legalBert    |  settlement    | letter    |  dealer   |  master   |   supplemental       |
| legalRoberta | License     |  Settlement   |  Contract   |  license   |   Trust       |

> LegalRoberta captures the case 

'The applicant submitted that her husband was subjected to treatment amounting to \<mask\> whilst in the custody of Adana Security Directorate'


| Model        | top1 | top2    |  top3   | top4    |  top5 |
| ------------ | ---- | --- | --- | --- | -------- |
| Bert    |  torture    |  rape   |  abuse   |  death   |     violence     |
| legalBert    |  torture    | detention    | arrest    |  rape   |   death       |
| legalRoberta | torture     |  abuse   |  insanity   |   cruelty  |    confinement      |

'Establishing a system for the identification and registration of \<mask\> animals and regarding the labeling of beef and beef products .':

| Model        | top1 | top2    |  top3   | top4    | top5 |
| ------------ | ---- | --- | --- | --- | -------- |
| Bert         |  farm    |  livestock   | draft    | domestic    |   wild       |
| legalBert    |   live   |  beef   |  farm   | pet    |      dairy    |
| legalRoberta | domestic     |  all   |  beef   |   wild  |    registered      |

## Load Pretrained Model

```python
from transformers import AutoTokenizer, AutoModel

tokenizer = AutoTokenizer.from_pretrained("saibo/legal-roberta-base")
model = AutoModel.from_pretrained("saibo/legal-roberta-base")
```

## Training data

The training data consists of 3 origins:

1. Patent Litigations (https://www.kaggle.com/uspto/patent-litigations): This dataset covers over 74k cases across 52 years and over 5 million relevant documents. 5 different files detail the litigating parties, their attorneys, results, locations, and dates.
    1. *1.57GB*
    2. abbrev:PL
    3. *clean 1.1GB*


2. Caselaw Access Project (CAP) (https://case.law/): Following 360 years of United States case law, Caselaw Access Project (CAP) API and bulk data services includes 40 million pages of U.S. court decisions and almost 6.5 million individual cases.
    1. *raw 5.6*
    2. abbrev:CAP
    3. *clean 2.8GB*
3. Google Patents Public Data (https://www.kaggle.com/bigquery/patents): The Google Patents Public Data contains a collection of publicly accessible, connected database tables for empirical analysis of the international patent system.
    1. *BigQuery (https://www.kaggle.com/sohier/beyond-queries-exploring-the-bigquery-api)*
    2. abbrev:GPPD(1.1GB,patents-public-data.uspto_oce_litigation.documents)
    3. *clean 1GB*

## Training procedure
We start from a pretrained ROBERTA-BASE model and fine-tune it on the legal corpus.

Fine-tuning configuration:
- lr = 5e-5(with lr decay, ends at 4.95e-8)
- num_epoch = 3
- Total steps = 446500
- Total_flos = 2.7365e18

Loss starts at 1.850 and ends at 0.880
The perplexity after fine-tuning on legal corpus = 2.2735

Device: 
2*GeForce GTX TITAN X computeCapability: 5.2 

## Eval results
We benchmarked the model on two downstream tasks: Multi-Label Classification for Legal Text and Catchphrase Retrieval with Legal Case Description. 

1.LMTC, Legal Multi-Label Text Classification 

Dataset:

Labels shape:    4271
Frequent labels: 739
Few labels:      3369
Zero labels:     163


Hyperparameters:
- lr: 1e-05
- batch_size: 4
- max_sequence_size: 512
- max_label_size: 15
- few_threshold: 50
- epochs: 10
- dropout:0.1
- early stop:yes
- patience: 3




## Limitations:
In the Masked Language Model showroom, the tokens have the prefix **Ġ**. This seems to be wired but I haven't yet been able to fix it.
I know in the case of BPE tokenizer(ROBERTA's tokenizer), the symbol Ġ means the end of a new token, and the majority of tokens in the vocabs of pre-trained tokenizers start with Ġ.

For example
```python
import transformers
tokenizer = transformers.RobertaTokenizer.from_pretrained('roberta-base')
print(tokenizer.tokenize('I love salad'))
```
Outputs:

```
['I', 'Ġlove', 'Ġsalad']
```

The pretraining of LegalRoBERTa was restricted by the size of legal corpora available and the number of pretraining steps is small compared to the popular domain adapted models. This makes legalRoBERTa significantly **under-trained**. 

## BibTeX entry and citation info




