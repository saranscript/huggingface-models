# XLNet Fine-tuned on SQuAD 2.0 Dataset
[XLNet](https://arxiv.org/abs/1906.08237) jointly developed by Google and CMU and fine-tuned on [SQuAD 2.0](https://rajpurkar.github.io/SQuAD-explorer/) for question answering down-stream task.

## Training Results (Metrics)
```
{
    "HasAns_exact": 74.7132253711201
    "HasAns_f1": 82.11971607032643
    "HasAns_total": 5928
    "NoAns_exact": 73.38940285954584
    "NoAns_f1": 73.38940285954584
    "NoAns_total": 5945
    "best_exact": 75.67590331003116
    "best_exact_thresh": -19.554906845092773
    "best_f1": 79.16215426779269
    "best_f1_thresh": -19.554906845092773
    "epoch": 4.0
    "exact": 74.05036637749515
    "f1": 77.74830934598614
    "total": 11873
}
```

## Results Comparison
| Metric | Paper     | Model     |
| ------ | --------- | --------- |
| **EM** | **78.46** | **75.68** (-2.78)      |
| **F1** | **81.33** | **79.16** (-2.17)|

Better fine-tuned models coming soon.

## How to Use
```
from transformers import XLNetForQuestionAnswering, XLNetTokenizerFast

model = XLNetForQuestionAnswering.from_pretrained('jkgrad/xlnet-base-squadv2)
tokenizer = XLNetTokenizerFast.from_pretrained('jkgrad/xlnet-base-squadv2')
```