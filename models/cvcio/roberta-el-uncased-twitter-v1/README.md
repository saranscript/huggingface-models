---
language: el
tags:
- roberta
- twitter
- Greek
widget:
 - text: "<mask>: μεγαλη υποχωρηση του ιικου φορτιου σε αττικη και θεσσαλονικη"
---

# Greek RoBERTa Uncased (v1)

Pretrained model on Greek language using a masked language modeling (MLM) objective using [Hugging Face's](https://huggingface.co/) [Transformers](https://github.com/huggingface/transformers) library. This model is case-sensitive and has no Greek diacritics (uncased, no-accents).

### Training data

This model was pretrained on almost 18M unique tweets, all Greek, collected between 2008-2021, from almost 450K distinct users.

### Preprocessing

The texts are tokenized using a byte version of Byte-Pair Encoding (BPE) and a vocabulary size of 50256. For the tokenizer we splited strings containing any numbers (ex. EU2019 ==> EU 2019). The tweet normalization logic described in the example listed bellow.

```python
import unicodedata
from transformers import pipeline

def normalize_tweet(tweet, do_lower = True, do_strip_accents = True, do_split_word_numbers = False, user_fill = '', url_fill = ''):
    # your tweet pre-processing logic goes here
    # example... 

    # remove extra spaces, escape HTML, replace non-standard punctuation
    # replace any @user with blank
    # replace any link with blank
    # explode hashtags to strings (ex. #EU2019 ==> EU 2019)
    # remove all emojis
    
    # if do_split_word_numbers:
    #     splited strings containing any numbers 
        
    # standardize punctuation
    # remove unicode symbols
    
    if do_lower:
        tweet = tweet.lower()
    if do_strip_accents:
        tweet = strip_accents(tweet)
    
    return tweet.strip()

def strip_accents(s):
    return ''.join(c for c in unicodedata.normalize('NFD', s)
                  if unicodedata.category(c) != 'Mn')

nlp = pipeline('fill-mask', model = 'cvcio/roberta-el-uncased-twitter-v1')

print(
    nlp(
        normalize_tweet(
            '<mask>: Μεγάλη υποχώρηση του ιικού φορτίου σε Αττική και Θεσσαλονίκη'
        )
    )
)
```

### Pretraining

The model was pretrained on a T4 GPU for 1.2M steps with a batch size of 96 and a sequence length of 96. The optimizer used is Adam with a learning rate of 1e-5, gradient accumulation steps of 8, learning rate warmup for 50000 steps and linear decay of the learning rate after.

### Authors

Dimitris Papaevagelou - [@andefined](https://github.com/andefined)

### About Us

[Civic Information Office](https://cvcio.org/) is a Non Profit Organization based in Athens, Greece focusing on creating technology and research products for the public interest.
