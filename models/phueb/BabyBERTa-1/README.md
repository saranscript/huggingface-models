---
language: en
tags:
- BabyBERTa
datasets:
- CHILDES
widget:
- text: "Look here. What is that <mask> ?"
- text: "Do you like your <mask> ?"
---

## BabyBERTA

### Overview

BabyBERTa is a light-weight version of RoBERTa trained on 5M words of American-English child-directed input.
It is intended for language acquisition research, on a single desktop with a single GPU - no high-performance computing infrastructure needed. 

The three provided models are randomly selected from 10 that were trained and reported in the paper. 

## Loading the tokenizer

BabyBERTa was trained with `add_prefix_space=True`, so it will not work properly with the tokenizer defaults.
For instance, to load the tokenizer for BabyBERTa-1, load it as follows:

```python
tokenizer = RobertaTokenizerFast.from_pretrained("phueb/BabyBERTa-1",
                                                 add_prefix_space=True)
```

### Hyper-Parameters

See the paper for details. 
All provided models were trained for 400K steps with a batch size of 16.
Importantly, BabyBERTa never predicts unmasked tokens during training - `unmask_prob` is set to  zero.


### Performance

BabyBerta was developed for learning grammatical knowledge from child-directed input. 
Its grammatical knowledge was evaluated using the [Zorro](https://github.com/phueb/Zorro) test suite.
The best model achieves an overall accuracy of 80.3, 
comparable to RoBERTa-base, which achieves an overall accuracy of 82.6 on the latest version of Zorro (as of October, 2021).
Both values differ slightly from those reported in the [CoNLL 2021 paper](https://aclanthology.org/2021.conll-1.49/). 
There are two reasons for this:
1. Performance of RoBERTa-base is slightly larger because the authors previously lower-cased all words in Zorro before evaluation.
Lower-casing of proper nouns is detrimental to RoBERTa-base because RoBERTa-base has likely been trained on proper nouns that are primarily title-cased.
In contrast, because BabyBERTa is not case-sensitive, its performance is not influenced by this change.
2. The latest version of Zorro no longer contains ambiguous content words such as "Spanish" which can be both a noun and an adjective.
 this resulted in a small reduction in the performance of BabyBERTa.
 
Overall Accuracy on Zorro:
 
| Model Name                             | Accuracy (holistic scoring)  | Accuracy (MLM-scoring) | 
|----------------------------------------|------------------------------|------------|
| [BabyBERTa-1][link-BabyBERTa-1]        | 80.3                         | 79.9       | 
| [BabyBERTa-2][link-BabyBERTa-2]        | 78.6                         | 78.2       | 
| [BabyBERTa-3][link-BabyBERTa-3]        | 74.5                         | 78.1       | 



### Additional Information

This model was trained by [Philip Huebner](https://philhuebner.com), currently at the [UIUC Language and Learning Lab](http://www.learninglanguagelab.org).

More info can be found [here](https://github.com/phueb/BabyBERTa).


[link-BabyBERTa-1]: https://huggingface.co/phueb/BabyBERTa-1
[link-BabyBERTa-2]: https://huggingface.co/phueb/BabyBERTa-2
[link-BabyBERTa-3]: https://huggingface.co/phueb/BabyBERTa-3
