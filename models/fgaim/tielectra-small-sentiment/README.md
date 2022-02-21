---
language: ti
widget:
- text: "ድምጻዊ ኣብርሃም ኣፈወርቂ ንዘልኣለም ህያው ኮይኑ ኣብ ልብና ይነብር"
metrics:
- f1
- precision
- recall
- accuracy
model-index:
- name: tielectra-small-sentiment
  results:
  - task:
      name: Text Classification
      type: text-classification
    metrics:
    - name: F1
      type: f1
      value: 0.8228962818003914
    - name: Precision
      type: precision
      value: 0.8055555555555556
    - name: Recall
      type: recall
      value: 0.841
    - name: Accuracy
      type: accuracy
      value: 0.819
---


# Sentiment Analysis for Tigrinya with TiELECTRA small

This model is a fine-tuned version of [TiELECTRA small](https://huggingface.co/fgaim/tielectra-small) on a YouTube comments Sentiment Analysis dataset for Tigrinya (Tela et al. 2020).


## Basic usage

```python
from transformers import pipeline

ti_sent = pipeline("sentiment-analysis", model="fgaim/tielectra-small-sentiment")
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

The model achieves the following results on the evaluation set:
- F1: 0.8229
- Precision: 0.8056
- Recall: 0.841
- Accuracy: 0.819
- Loss: 0.4299

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
  publisher= {WiNLP 2021/EMNLP 2021}
}
```


## References

```
Tela, A., Woubie, A. and Hautamäki, V. 2020.
Transferring Monolingual Model to Low-Resource Language: The Case of Tigrinya.
ArXiv, abs/2006.07698.
```
