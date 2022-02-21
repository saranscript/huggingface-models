---
tags:
- glove
- gensim
license: PDDL
---

# Glove Twitter 

Pre-trained glove vectors based on 2B tweets, 27B tokens, 1.2M vocab, uncased.

Read more:
* https://nlp.stanford.edu/projects/glove/
* https://nlp.stanford.edu/pubs/glove.pdf

## Example Usage

```python
import gensim.downloader as api
model = api.load("glove-twitter-25", from_hf=True)
model.most_similar(positive=['fruit', 'flower'], topn=1)

"""
Output:

[('cherry', 0.9183273911476135)]
"""
``` 