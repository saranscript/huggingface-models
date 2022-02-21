# DPRQuestionEncoder for TriviaQA

## dpr-question_encoder-single-trivia-base

Dense Passage Retrieval (`DPR`)

Vladimir Karpukhin, Barlas Oğuz, Sewon Min, Patrick Lewis, Ledell Wu, Sergey Edunov, Danqi Chen, Wen-tau Yih, [Dense Passage Retrieval for Open-Domain Question Answering](https://arxiv.org/abs/2004.04906), EMNLP 2020.

This model is the question encoder of DPR trained solely on TriviaQA (single-trivia) using the [official implementation of DPR](https://github.com/facebookresearch/DPR).

Disclaimer: This model is not from the authors of DPR, but my reproduction. The authors did not release the DPR weights trained solely on TriviaQA. I hope this model checkpoint can be helpful for those who want to use DPR trained only on TriviaQA.

## Performance

The following is the answer recall rate measured using PyTorch 1.4.0 and transformers 4.5.0.

The values in parentheses are those reported in the paper.

| Top-K Passages | TriviaQA Dev | TriviaQA Test |
|----------------|--------------|---------------|
| 1              | 54.27        | 54.41         |
| 5              | 71.11        | 70.99         |
| 20             | 79.53        | 79.31 (79.4)  |
| 50             | 82.72        | 82.99         |
| 100            | 85.07        | 84.99 (85.0)  |

## How to Use

Using `AutoModel` does not properly detect whether the checkpoint is for `DPRContextEncoder` or `DPRQuestionEncoder`.

Therefore, please specify the exact class to use the model.

```python
from transformers import DPRQuestionEncoder, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("soheeyang/dpr-question_encoder-single-trivia-base")
question_encoder = DPRQuestionEncoder.from_pretrained("soheeyang/dpr-question_encoder-single-trivia-base")

data = tokenizer("question comes here", return_tensors="pt")
question_embedding = question_encoder(**data).pooler_output  # embedding vector for question
```
