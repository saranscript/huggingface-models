---
language: de
tags:
- summarization
datasets:
- mlsum
---

# mT5-small fine-tuned on German MLSUM
This model was finetuned for 3 epochs with a max_len (input) of 768 tokens and target_max_len of 192 tokens.  
It was fine-tuned on all German articles present in the train split of the [MLSUM dataset](https://huggingface.co/datasets/mlsum) having less than 384 "words" after splitting on whitespace, which resulted in 80249 articles.  
The exact expression to filter the dataset was the following:
```python
dataset = dataset.filter(lambda e: len(e['text'].split()) < 384)
```

## Evaluation results
The fine-tuned model was evaluated on 2000 random articles from the validation set.
Mean [f1 ROUGE scores](https://github.com/pltrdy/rouge) were calculated for both the fine-tuned model and the lead-3 baseline (which simply produces the leading three sentences of the document) and are presented in the following table.

| Model         | Rouge-1 | Rouge-2  | Rouge-L |
| ------------- |:-------:| --------:| -------:|
| mt5-small     | 0.399   | 0.318    | 0.392   |
| lead-3        | 0.343   | 0.263    | 0.341   |