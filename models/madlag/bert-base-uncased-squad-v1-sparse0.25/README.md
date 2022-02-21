---
language: en
thumbnail: 
license: mit
tags:
- question-answering
- bert
- bert-base
datasets:
- squad
metrics:
- squad
widget:
- text: "Where is located the Eiffel Tower ?"
  context: "The Eiffel Tower is a wrought-iron lattice tower on the Champ de Mars in Paris, France. It is named after the engineer Gustave Eiffel, whose company designed and built the tower."
- text: "Who is Frederic Chopin?"
  context: "Frédéric François Chopin, born Fryderyk Franciszek Chopin (1 March 1810 – 17 October 1849), was a Polish composer and virtuoso pianist of the Romantic era who wrote primarily for solo piano."
---

## BERT-base uncased model fine-tuned on SQuAD v1

This model is [block-sparse](https://github.com/huggingface/pytorch_block_sparse).

That means that with the right runtime it can run roughly 3x faster than an dense network, with 25% of the original weights. 

This of course has some impact on the accuracy (see below).

It uses a modified version of Victor Sanh [Movement Pruning](https://arxiv.org/abs/2005.07683) method.

This model was fine-tuned from the HuggingFace [BERT](https://www.aclweb.org/anthology/N19-1423/) base uncased checkpoint on [SQuAD1.1](https://rajpurkar.github.io/SQuAD-explorer).
This model is case-insensitive: it does not make a difference between english and English.

## Details

| Dataset  | Split | # samples |
| -------- | ----- | --------- |
| SQuAD1.1 | train | 90.6K      |
| SQuAD1.1 | eval  | 11.1k     |


### Fine-tuning
- Python: `3.8.5`

- Machine specs: 

  `CPU: Intel(R) Core(TM) i7-6700K CPU`
  
  `Memory: 64 GiB`

  `GPUs: 1 GeForce GTX 3090, with 24GiB memory`
  
  `GPU driver: 455.23.05, CUDA: 11.1`


### Results

**Model size**: `418M`

| Metric | # Value   | # Original ([Table 2](https://www.aclweb.org/anthology/N19-1423.pdf))|
| ------ | --------- | --------- |
| **EM** | **74.82** | **80.8** |
| **F1** | **83.7** | **88.5** |

Note that the above results didn't involve any hyperparameter search.

## Example Usage

```python
from transformers import pipeline

qa_pipeline = pipeline(
    "question-answering",
    model="madlag/bert-base-uncased-squad-v1-sparse0.25",
    tokenizer="madlag/bert-base-uncased-squad-v1-sparse0.25"
)

predictions = qa_pipeline({
    'context': "Frédéric François Chopin, born Fryderyk Franciszek Chopin (1 March 1810 – 17 October 1849), was a Polish composer and virtuoso pianist of the Romantic era who wrote primarily for solo piano.",
    'question': "Who is Frederic Chopin?",
})

print(predictions)
