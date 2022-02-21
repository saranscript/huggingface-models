# rdr-ctx_encoder-single-trivia-base

Reader-Distilled Retriever (`RDR`)

Sohee Yang and Minjoon Seo, [Is Retriever Merely an Approximator of Reader?](https://arxiv.org/abs/2010.10999), arXiv 2020

The paper proposes to distill the reader into the retriever so that the retriever absorbs the strength of the reader while keeping its own benefit. The model is a DPR retriever further finetuned using knowledge distillation from the DPR reader. Using this approach, the answer recall rate increases by a large margin, especially at small numbers of top-k.

This model is the context encoder of RDR trained solely on TriviaQA (single-trivia). This model is trained by the authors and is the official checkpoint of RDR.

## Performance

The following is the answer recall rate measured using PyTorch 1.4.0 and transformers 4.5.0.

For the values of DPR, those in parentheses are directly taken from the paper. The values without parentheses are reported using the reproduction of DPR that consists of [this context encoder](https://huggingface.co/soheeyang/dpr-ctx_encoder-single-trivia-base) and [this queston encoder](https://huggingface.co/soheeyang/dpr-question_encoder-single-trivia-base).

|             | Top-K Passages   | 1         | 5         | 20        | 50        | 100       |
|-------------|------------------|-----------|-----------|-----------|-----------|-----------|
|**TriviaQA Dev** | **DPR**              | 54.27     | 71.11     | 79.53     | 82.72     | 85.07     |
|             | **RDR (This Model)** | **61.84** | **75.93** | **82.56** | **85.35** | **87.00** |
|**TriviaQA Test**| **DPR**              | 54.41     | 70.99     | 79.31 (79.4)     | 82.90     | 84.99 (85.0)     |
|             | **RDR (This Model)** | **62.56** | **75.92** | **82.52** | **85.64** | **87.26** |

## How to Use

RDR shares the same architecture with DPR. Therefore, It uses `DPRContextEncoder` as the model class.

Using `AutoModel` does not properly detect whether the checkpoint is for `DPRContextEncoder` or `DPRQuestionEncoder`.

Therefore, please specify the exact class to use the model.

```python
from transformers import DPRContextEncoder, AutoTokenizer

tokenizer = AutoTokenizer.from_pretrained("soheeyang/rdr-ctx_encoder-single-trivia-base")
ctx_encoder = DPRContextEncoder.from_pretrained("soheeyang/rdr-ctx_encoder-single-trivia-base")

data = tokenizer("context comes here", return_tensors="pt")
ctx_embedding = ctx_encoder(**data).pooler_output  # embedding vector for context
```
