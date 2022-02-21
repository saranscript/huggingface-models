---
language: es
datasets:
- stsb_multi_mt
tags:
- sentence-similarity
- sentence-transformers
---


This is a test model that was fine-tuned using the Spanish datasets from [stsb_multi_mt](https://huggingface.co/datasets/stsb_multi_mt) in order to understand and benchmark STS models.

## Model and training data description

This model was built taking `distiluse-base-multilingual-cased-v1` and training it on a Semantic Textual Similarity task using a modified version of the training script for STS from Sentece Transformers (the modified script is included in the repo). It was trained using the Spanish datasets from [stsb_multi_mt](https://huggingface.co/datasets/stsb_multi_mt) which are the STSBenchmark datasets automatically translated to other languages using deepl.com. Refer to the dataset repository for more details.

## Intended uses & limitations

This model was built just as a proof-of-concept on STS fine-tuning using Spanish data and no specific use other than getting a sense on how this training works.

## How to use

You may use it as any other STS trained model to extract sentence embeddings. Check Sentence Transformers documentation. 

## Training procedure

This model was trained using this [Colab Notebook](https://colab.research.google.com/drive/1ZNjDMFdy_lKhnD9BtbqzSbQ4LNz638ZA?usp=sharing)

## Evaluation results

Evaluating `distiluse-base-multilingual-cased-v1` on the Spanish test dataset before training results in:

```
2021-07-06 17:44:46 - EmbeddingSimilarityEvaluator: Evaluating the model on  dataset:
2021-07-06 17:45:00 - Cosine-Similarity :	Pearson: 0.7662	Spearman: 0.7583
2021-07-06 17:45:00 - Manhattan-Distance:	Pearson: 0.7805	Spearman: 0.7772
2021-07-06 17:45:00 - Euclidean-Distance:	Pearson: 0.7816	Spearman: 0.7778
2021-07-06 17:45:00 - Dot-Product-Similarity:	Pearson: 0.6610	Spearman: 0.6536
```

While the fine-tuned version with the defaults of the training script and the Spanish training dataset results in:

```
2021-07-06 17:49:22 - EmbeddingSimilarityEvaluator: Evaluating the model on stsb-multi-mt-test dataset:
2021-07-06 17:49:24 - Cosine-Similarity :	Pearson: 0.8265	Spearman: 0.8207
2021-07-06 17:49:24 - Manhattan-Distance:	Pearson: 0.8131	Spearman: 0.8190
2021-07-06 17:49:24 - Euclidean-Distance:	Pearson: 0.8129	Spearman: 0.8190
2021-07-06 17:49:24 - Dot-Product-Similarity:	Pearson: 0.7773	Spearman: 0.7692
```

In our [STS Evaluation repository](https://github.com/eduardofv/sts_eval) we compare the performance of this model with other models from Sentence Transformers and Tensorflow Hub using the standard STSBenchmark and the 2017 STSBenchmark Task 3 for Spanish.


## Resources

- Training dataset [stsb_multi_mt](https://huggingface.co/datasets/stsb_multi_mt)
- Sentence Transformers [Semantic Textual Similarity](https://www.sbert.net/examples/training/sts/README.html)
- Check [sts_eval](https://github.com/eduardofv/sts_eval) for a comparison with Tensorflow and Sentence-Transformers models
- Check the [development environment to run the scripts and evaluation](https://github.com/eduardofv/ai-denv)
