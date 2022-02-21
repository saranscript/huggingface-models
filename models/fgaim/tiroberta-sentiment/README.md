---
language: ti
widget:
- text: "ድምጻዊ ኣብርሃም ኣፈወርቂ ንዘልኣለም ህያው ኮይኑ ኣብ ልብና ይነብር"
datasets:
- TLMD
metrics:
- accuracy
- f1
- precision
- recall
model-index:
- name: tiroberta-sentiment
  results:
  - task:
      name: Text Classification
      type: text-classification
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.828
    - name: F1
      type: f1
      value: 0.8476527900797165
    - name: Precision
      type: precision
      value: 0.760731319554849
    - name: Recall
      type: recall
      value: 0.957
---


# Sentiment Analysis for Tigrinya with TiRoBERTa

This model is a fine-tuned version of [TiRoBERTa](https://huggingface.co/fgaim/roberta-base-tigrinya) on a YouTube comments Sentiment Analysis dataset for Tigrinya (Tela et al. 2020).


## Basic usage

```python
from transformers import pipeline

ti_sent = pipeline("sentiment-analysis", model="fgaim/tiroberta-sentiment")
ti_sent("ድምጻዊ ኣብርሃም ኣፈወርቂ ንዘልኣለም ህያው ኮይኑ ኣብ ልብና ይነብር")
```


## Training

### Hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Results

It achieves the following results on the evaluation set:
- F1: 0.8477
- Precision: 0.7607
- Recall: 0.957
- Accuracy: 0.828
- Loss: 0.6796

### Framework versions

- Transformers 4.10.3
- Pytorch 1.9.0+cu111
- Datasets 1.10.2
- Tokenizers 0.10.1


## Citation

If you use this model in your product or research, please cite as follows:

```
@article{Fitsum2021TiPLMs,
  author={Fitsum Gaim and Wonsuk Yang and Jong C. Park},
  title={Monolingual Pre-trained Language Models for Tigrinya},
  year=2021,
  publisher={WiNLP 2021/EMNLP 2021}
}
```


## References

```
Tela, A., Woubie, A. and Hautamäki, V. 2020.
Transferring Monolingual Model to Low-Resource Language: The Case of Tigrinya.
ArXiv, abs/2006.07698.
```
