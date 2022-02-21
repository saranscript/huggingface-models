---
language: en
thumbnail:
license: mit
tags:
- question-answering
- 
- 
datasets:
- squad_v2
metrics:
- squad_v2
widget:
- text: "Where is the Eiffel Tower located?"
  context: "The Eiffel Tower is a wrought-iron lattice tower on the Champ de Mars in Paris, France. It is named after the engineer Gustave Eiffel, whose company designed and built the tower."
- text: "Who is Frederic Chopin?"
  context: "Frédéric François Chopin, born Fryderyk Franciszek Chopin (1 March 1810 – 17 October 1849), was a Polish composer and virtuoso pianist of the Romantic era who wrote primarily for solo piano."
---

## bert-large-uncased-whole-word-masking model fine-tuned on SQuAD v2

This model was created using the [nn_pruning](https://github.com/huggingface/nn_pruning) python library: the **linear layers contains 25.0%** of the original  weights.



The model contains **32.0%** of the original weights **overall** (the embeddings account for a significant part of the model, and they are not pruned by this method).

With a simple resizing of the linear matrices it ran **2.15x as fast as bert-large-uncased-whole-word-masking** on the evaluation.
This is possible because the pruning method lead to structured matrices: to visualize them, hover below on the plot to see the non-zero/zero parts of each matrix.

<div class="graph"><script src="/madlag/bert-large-uncased-wwm-squadv2-x2.15-f83.2-d25-hybrid-v1/raw/main/model_card/density_info.js" id="d55f6096-07eb-4cc1-b284-90ec6ced516c"></script></div>

In terms of accuracy, its **F1 is 83.22**, compared with 85.85 for bert-large-uncased-whole-word-masking, a **F1 drop of 2.63**.

## Fine-Pruning details
This model was fine-tuned from the HuggingFace [model](https://huggingface.co/bert-large-uncased-whole-word-masking) checkpoint on [SQuAD2.0](https://rajpurkar.github.io/SQuAD-explorer), and distilled from the model [madlag/bert-large-uncased-whole-word-masking-finetuned-squadv2](https://huggingface.co/madlag/bert-large-uncased-whole-word-masking-finetuned-squadv2).
This model is case-insensitive: it does not make a difference between english and English.

A side-effect of the block pruning is that some of the attention heads are completely removed: 155 heads were removed on a total of 384 (40.4%).
Here is a detailed view on how the remaining heads are distributed in the network after pruning.
<div class="graph"><script src="/madlag/bert-large-uncased-wwm-squadv2-x2.15-f83.2-d25-hybrid-v1/raw/main/model_card/pruning_info.js" id="a474f11e-7e05-495e-bb21-4af0edfb6661"></script></div>

## Details of the SQuAD1.1 dataset

| Dataset  | Split | # samples |
| -------- | ----- | --------- |
| SQuAD 2.0 | train | 130.0K      |
| SQuAD 2.0 | eval  | 11.9k     |

### Fine-tuning
- Python: `3.8.5`

- Machine specs:

```CPU: Intel(R) Core(TM) i7-6700K CPU
Memory: 64 GiB
GPUs: 1 GeForce GTX 3090, with 24GiB memory
GPU driver: 455.23.05, CUDA: 11.1
```

### Results

**Pytorch model file size**: `1119MB` (original BERT: `1228.0MB`)

| Metric | # Value   | # Original ([Table 2](https://www.aclweb.org/anthology/N19-1423.pdf))| Variation |
| ------ | --------- | --------- | --------- |
| **EM** | **80.19** | **82.83** | **-3.64**|
| **F1** | **83.22** | **85.85** | **-2.63**|

```
{
    "HasAns_exact": 76.48448043184885,
    "HasAns_f1": 82.55514100819374,
    "HasAns_total": 5928,
    "NoAns_exact": 83.8856181665265,
    "NoAns_f1": 83.8856181665265,
    "NoAns_total": 5945,
    "best_exact": 80.19034784805862,
    "best_exact_thresh": 0.0,
    "best_f1": 83.22133208932635,
    "best_f1_thresh": 0.0,
    "exact": 80.19034784805862,
    "f1": 83.22133208932645,
    "total": 11873
}
```

## Example Usage
Install nn_pruning: it contains the optimization script, which just pack the linear layers into smaller ones by removing empty rows/columns.

`pip install nn_pruning`

Then you can use the `transformers library` almost as usual: you just have to call `optimize_model` when the pipeline has loaded.

```python
from transformers import pipeline
from nn_pruning.inference_model_patcher import optimize_model

qa_pipeline = pipeline(
    "question-answering",
    model="madlag/bert-large-uncased-wwm-squadv2-x2.15-f83.2-d25-hybrid-v1",
    tokenizer="madlag/bert-large-uncased-wwm-squadv2-x2.15-f83.2-d25-hybrid-v1"
)

print("bert-large-uncased-whole-word-masking parameters: 497.0M")
print(f"Parameters count (includes only head pruning, not feed forward pruning)={int(qa_pipeline.model.num_parameters() / 1E6)}M")
qa_pipeline.model = optimize_model(qa_pipeline.model, "dense")

print(f"Parameters count after complete optimization={int(qa_pipeline.model.num_parameters() / 1E6)}M")
predictions = qa_pipeline({
    'context': "Frédéric François Chopin, born Fryderyk Franciszek Chopin (1 March 1810 – 17 October 1849), was a Polish composer and virtuoso pianist of the Romantic era who wrote primarily for solo piano.",
    'question': "Who is Frederic Chopin?",
})
print("Predictions", predictions)
```