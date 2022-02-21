---
language: en
thumbnail:
license: mit
tags:
- question-answering
- 
- 
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

This model was created using the [nn_pruning](https://github.com/huggingface/nn_pruning) python library: the **linear layers contains 15.0%** of the original  weights.



The model contains **34.0%** of the original weights **overall** (the embeddings account for a significant part of the model, and they are not pruned by this method).

With a simple resizing of the linear matrices it ran **2.32x as fast as bert-base-uncased** on the evaluation.
This is possible because the pruning method lead to structured matrices: to visualize them, hover below on the plot to see the non-zero/zero parts of each matrix.

<div class="graph"><script src="/madlag/bert-base-uncased-squadv1-x2.32-f86.6-d15-hybrid-v1/raw/main/model_card/density_info.js" id="1ff1ba08-69d3-4a20-9f29-494033c72860"></script></div>

In terms of accuracy, its **F1 is 86.64**, compared with 88.5 for bert-base-uncased, a **F1 drop of 1.86**.

## Fine-Pruning details
This model was fine-tuned from the HuggingFace [model](https://huggingface.co/bert-base-uncased) checkpoint on [SQuAD1.1](https://rajpurkar.github.io/SQuAD-explorer), and distilled from the model [bert-large-uncased-whole-word-masking-finetuned-squad](https://huggingface.co/bert-large-uncased-whole-word-masking-finetuned-squad)
This model is case-insensitive: it does not make a difference between english and English.

A side-effect of the block pruning is that some of the attention heads are completely removed: 63 heads were removed on a total of 144 (43.8%).
Here is a detailed view on how the remaining heads are distributed in the network after pruning.
<div class="graph"><script src="/madlag/bert-base-uncased-squadv1-x2.32-f86.6-d15-hybrid-v1/raw/main/model_card/pruning_info.js" id="e092ee84-28af-4821-8127-11914f68e306"></script></div>

## Details of the SQuAD1.1 dataset

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

**Pytorch model file size**: `368MB` (original BERT: `420MB`)

| Metric | # Value   | # Original ([Table 2](https://www.aclweb.org/anthology/N19-1423.pdf))| Variation |
| ------ | --------- | --------- | --------- |
| **EM** | **78.77** | **80.8** | **-2.03**|
| **F1** | **86.64** | **88.5** | **-1.86**|

## Example Usage
Install nn_pruning: it contains the optimization script, which just pack the linear layers into smaller ones by removing empty rows/columns.

`pip install nn_pruning`

Then you can use the `transformers library` almost as usual: you just have to call `optimize_model` when the pipeline has loaded.

```python
from transformers import pipeline
from nn_pruning.inference_model_patcher import optimize_model

qa_pipeline = pipeline(
    "question-answering",
    model="madlag/bert-base-uncased-squadv1-x2.32-f86.6-d15-hybrid-v1",
    tokenizer="madlag/bert-base-uncased-squadv1-x2.32-f86.6-d15-hybrid-v1"
)

print("bert-base-uncased parameters: 165.0M")
print(f"Parameters count (includes only head pruning, not feed forward pruning)={int(qa_pipeline.model.num_parameters() / 1E6)}M")
qa_pipeline.model = optimize_model(qa_pipeline.model, "dense")

print(f"Parameters count after complete optimization={int(qa_pipeline.model.num_parameters() / 1E6)}M")
predictions = qa_pipeline({
    'context': "Frédéric François Chopin, born Fryderyk Franciszek Chopin (1 March 1810 – 17 October 1849), was a Polish composer and virtuoso pianist of the Romantic era who wrote primarily for solo piano.",
    'question': "Who is Frederic Chopin?",
})
print("Predictions", predictions)
```