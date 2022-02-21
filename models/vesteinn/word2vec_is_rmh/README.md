---
license: agpl-3.0
language: 
- is
---
# word2vec model trained on Icelandic

This model is trained on the lemmas of the Icelandic Gigaword Corpus version 20.05. It is trained using the gensim package, version 4.1.0. and parameters were set to default (100 dimensions, windows size 5)

This model can not be loaded directly since it uses gensim, clone the repository and run the following to use it.

```python
import gensim
model = gensim.models.Word2Vec.load("./rmh.w2v.model")
```

## Example output

```bash
In [6]: model.wv.most_similar("england")
Out[6]: 
[('wales', 0.8113704323768616),
 ('skotland', 0.7611601948738098),
 ('bretlandseyjar', 0.7280426621437073),
 ('gateshead', 0.6975484490394592),
 ('ástralía', 0.6963852047920227),
 ('eastbourne', 0.6939234137535095),
 ('englandi', 0.6908402442932129),
 ('bath', 0.6849308013916016),
 ('lynndie', 0.6826340556144714),
 ('glasgow', 0.6815919876098633)]

In [7]: model.wv.most_similar("ísland")
Out[7]: 
[('norðurlönd', 0.6843729615211487),
 ('land', 0.6696498990058899),
 ('íslendingur', 0.6645756959915161),
 ('íslenskur', 0.6627770662307739),
 ('hérlendis', 0.6609933376312256),
 ('íslandi', 0.6514216661453247),
 ('evrópa', 0.6289927959442139),
 ('fróðskaparsetur', 0.6046777367591858),
 ('evrópuland', 0.5911464095115662),
 ('bandaríkin', 0.5906434655189514)]

```


