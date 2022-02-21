---
language:
- da
license: mit
model-index:
- name: contract-ner-model-da
  results: []
widget:
- "Medarbejderen starter arbejdet den 1. januar 2020 og afslutter arbejdet den 21. januar 2020. Den ugentlige arbejdstid er 37 timer, og medarbejderen bliver aflønnet med 23.000,00 kr. om måneden. Arbejdsstedet er Supervej 21, 2000 Frederiksberg."
inference:
  parameters:
    aggregation_strategy: "first"
---

# contract-ner-model-da

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on a custom contracts dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0026
- Micro F1: 0.9297

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 919
- num_epochs: 500

### Training results

| Training Loss | Epoch | Step | Validation Loss | Micro F1 |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.8971        | 0.24  | 200  | 0.0205          | 0.0      |
| 0.0173        | 0.48  | 400  | 0.0100          | 0.2921   |
| 0.0092        | 0.73  | 600  | 0.0065          | 0.7147   |
| 0.0063        | 0.97  | 800  | 0.0046          | 0.8332   |
| 0.0047        | 1.21  | 1000 | 0.0047          | 0.8459   |
| 0.0042        | 1.45  | 1200 | 0.0039          | 0.8694   |
| 0.0037        | 1.69  | 1400 | 0.0035          | 0.8888   |
| 0.0032        | 1.93  | 1600 | 0.0035          | 0.8840   |
| 0.0025        | 2.18  | 1800 | 0.0029          | 0.8943   |
| 0.0023        | 2.42  | 2000 | 0.0024          | 0.9104   |
| 0.0023        | 2.66  | 2200 | 0.0032          | 0.8808   |
| 0.0021        | 2.9   | 2400 | 0.0022          | 0.9338   |
| 0.0018        | 3.14  | 2600 | 0.0020          | 0.9315   |
| 0.0015        | 3.39  | 2800 | 0.0026          | 0.9297   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.8.1+cu101
- Datasets 1.12.1
- Tokenizers 0.10.3