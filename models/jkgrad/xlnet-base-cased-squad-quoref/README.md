# XLNet Fine-tuned on SQuAD / Quoref Dataset
[XLNet](https://arxiv.org/abs/1906.08237) jointly developed by Google and CMU and fine-tuned on [SQuAD / SQuAD 2.0](https://rajpurkar.github.io/SQuAD-explorer/) and [Quoref](https://leaderboard.allenai.org/quoref) for question answering down-stream task. 

## Evaluation Result on Quoref
```
{
    "exact_match": 73.65591397848462,
    "f1": 77.9981532789881
}
```

## Results Comparison on Quoref
| Metric | XLNet Base Line | Model FT on SQuAD    |
| ------ | --------- | --------- |
| **EM** | **61.88** | **73.66** (+11.78)      |
| **F1** | **70.51** | **78.00** (+7.49)|

## How to Use
```
from transformers import XLNetForQuestionAnswering, XLNetTokenizerFast

model = XLNetForQuestionAnswering.from_pretrained('jkgrad/xlnet-base-cased-squad-quoref)
tokenizer = XLNetTokenizerFast.from_pretrained('jkgrad/xlnet-base-cased-squad-quoref')
```