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
- text: "Where is the Eiffel Tower located?"
  context: "The Eiffel Tower is a wrought-iron lattice tower on the Champ de Mars in Paris, France. It is named after the engineer Gustave Eiffel, whose company designed and built the tower."
- text: "Who is Frederic Chopin?"
  context: "Frédéric François Chopin, born Fryderyk Franciszek Chopin (1 March 1810 – 17 October 1849), was a Polish composer and virtuoso pianist of the Romantic era who wrote primarily for solo piano."
---

## BERT-base uncased model fine-tuned on SQuAD v1

This model is block sparse: the **linear** layers contains **31.7%** of the original weights.


The model contains **47.0%** of the original weights **overall**.

The training use a modified version of Victor Sanh [Movement Pruning](https://arxiv.org/abs/2005.07683) method.

That means that with the [block-sparse](https://github.com/huggingface/pytorch_block_sparse) runtime it ran **1.12x** faster than an dense networks on the evaluation, at the price of some impact on the accuracy (see below).



This model was fine-tuned from the HuggingFace [BERT](https://www.aclweb.org/anthology/N19-1423/) base uncased checkpoint on [SQuAD1.1](https://rajpurkar.github.io/SQuAD-explorer), and distilled from the equivalent model [csarron/bert-base-uncased-squad-v1](https://huggingface.co/csarron/bert-base-uncased-squad-v1).
This model is case-insensitive: it does not make a difference between english and English.

## Pruning details
A side-effect of the block pruning is that some of the attention heads are completely removed: 80 heads were removed on a total of 144 (55.6%).

Here is a detailed view on how the remaining heads are distributed in the network after pruning.

![Pruning details](https://huggingface.co/madlag/bert-base-uncased-squad1.1-block-sparse-0.32-v1/raw/main/model_card/pruning.svg)

## Density plot

<script src="/madlag/bert-base-uncased-squad1.1-block-sparse-0.32-v1/raw/main/model_card/density.js" id="79005f4a-723c-4bf8-bc7f-5ad11676be6c"></script>

## Details

| Dataset  | Split | # samples |
| -------- | ----- | --------- |
| SQuAD1.1 | train | 90.6K      |
| SQuAD1.1 | eval  | 11.1k     |

### Fine-tuning
- Python: `3.8.5`

- Machine specs: 

```CPU: Intel(R) Core(TM) i7-6700K CPU
Memory: 64 GiB
GPUs: 1 GeForce GTX 3090, with 24GiB memory
GPU driver: 455.23.05, CUDA: 11.1
```


### Results

**Pytorch model file size**: `355M` (original BERT: `438M`)

| Metric | # Value   | # Original ([Table 2](https://www.aclweb.org/anthology/N19-1423.pdf))|
| ------ | --------- | --------- |
| **EM** | **79.04** | **80.8** |
| **F1** | **86.70** | **88.5** |

## Example Usage

```python
from transformers import pipeline

qa_pipeline = pipeline(
    "question-answering",
    model="madlag/bert-base-uncased-squad1.1-block-sparse-0.32-v1",
    tokenizer="madlag/bert-base-uncased-squad1.1-block-sparse-0.32-v1"
)

predictions = qa_pipeline({
    'context': "Frédéric François Chopin, born Fryderyk Franciszek Chopin (1 March 1810 – 17 October 1849), was a Polish composer and virtuoso pianist of the Romantic era who wrote primarily for solo piano.",
    'question': "Who is Frederic Chopin?",
})

print(predictions)
```