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

This model was created using the [nn_pruning](https://github.com/huggingface/nn_pruning) python library: the **linear layers contains 16.0%** of the original  weights.



The model contains **24.0%** of the original weights **overall** (the embeddings account for a significant part of the model, and they are not pruned by this method).

With a simple resizing of the linear matrices it ran **2.63x as fast as bert-large-uncased-whole-word-masking** on the evaluation.
This is possible because the pruning method lead to structured matrices: to visualize them, hover below on the plot to see the non-zero/zero parts of each matrix.

<div class="graph"><script src="/madlag/bert-large-uncased-wwm-squadv2-x2.63-f82.6-d16-hybrid-v1/raw/main/model_card/density_info.js" id="0e65059e-a61d-4561-947e-b8f47b818bb8"></script></div>

In terms of accuracy, its **F1 is 82.57**, compared with 85.85 for bert-large-uncased-whole-word-masking, a **F1 drop of 3.28**.

## Fine-Pruning details
This model was fine-tuned from the HuggingFace [model](https://huggingface.co/bert-large-uncased-whole-word-masking) checkpoint on [SQuAD2.0](https://rajpurkar.github.io/SQuAD-explorer), and distilled from the model [madlag/bert-large-uncased-whole-word-masking-finetuned-squadv2](https://huggingface.co/madlag/bert-large-uncased-whole-word-masking-finetuned-squadv2).
This model is case-insensitive: it does not make a difference between english and English.

A side-effect of the block pruning is that some of the attention heads are completely removed: 190 heads were removed on a total of 384 (49.5%).
Here is a detailed view on how the remaining heads are distributed in the network after pruning.
<div class="graph"><script src="/madlag/bert-large-uncased-wwm-squadv2-x2.63-f82.6-d16-hybrid-v1/raw/main/model_card/pruning_info.js" id="f7ae9ec9-d050-46d0-b237-3025165e9504"></script></div>

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

**Pytorch model file size**: `1084MB` (original BERT: `1228.0MB`)

| Metric | # Value   | # Original ([Table 2](https://www.aclweb.org/anthology/N19-1423.pdf))| Variation |
| ------ | --------- | --------- | --------- |
| **EM** | **79.70** | **82.83** | **-4.13**|
| **F1** | **82.57** | **85.85** | **-3.28**|

```
{
    "HasAns_exact": 74.8144399460189,
    "HasAns_f1": 80.555306012496,
    "HasAns_total": 5928,
    "NoAns_exact": 84.57527333894029,
    "NoAns_f1": 84.57527333894029,
    "NoAns_total": 5945,
    "best_exact": 79.70184452118251,
    "best_exact_thresh": 0.0,
    "best_f1": 82.56816761071966,
    "best_f1_thresh": 0.0,
    "exact": 79.70184452118251,
    "f1": 82.56816761071981,
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
    model="madlag/bert-large-uncased-wwm-squadv2-x2.63-f82.6-d16-hybrid-v1",
    tokenizer="madlag/bert-large-uncased-wwm-squadv2-x2.63-f82.6-d16-hybrid-v1"
)

print("bert-large-uncased-whole-word-masking parameters: 445.0M")
print(f"Parameters count (includes only head pruning, not feed forward pruning)={int(qa_pipeline.model.num_parameters() / 1E6)}M")
qa_pipeline.model = optimize_model(qa_pipeline.model, "dense")

print(f"Parameters count after complete optimization={int(qa_pipeline.model.num_parameters() / 1E6)}M")
predictions = qa_pipeline({
    'context': "Frédéric François Chopin, born Fryderyk Franciszek Chopin (1 March 1810 – 17 October 1849), was a Polish composer and virtuoso pianist of the Romantic era who wrote primarily for solo piano.",
    'question': "Who is Frederic Chopin?",
})
print("Predictions", predictions)
```