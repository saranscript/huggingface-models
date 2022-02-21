---
language:
- lu
tags:
- text
- MLM
license: mit
---

## BERT Medium for Luxembourgish

Created from a dataset with 1M Luxembourgish sentences from Wikipedia. Corpus has approx. 16M words.

The MLM objective was trained. The BERT model has parameters `L=8` and `H=512`. Vocabulary has 70K word pieces.

Final loss scores, after 3 epochs:

- Final train loss: 4.230
- Final train perplexity: 68.726
- Final validation loss: 4.074
- Final validation perplexity: 58.765
