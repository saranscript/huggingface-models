---
license: mit
tags:
- generated_from_trainer
model-index:
- name: deberta-pretrained-large
  results: []
---

# Austin MeDeBERTa

This model was developed using further MLM pre-training on [microsoft/deberta-base](https://huggingface.co/microsoft/deberta-base), using a dataset of 1.1M clinical notes from the Austin Health EMR. The notes span discharge summaries, inpatient notes, radiology reports and histopathology reports.

## Model description

This is the base version of the original DeBERTa model. The architecture and tokenizer are unchanged. 

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 9
- eval_batch_size: 9
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step   | Validation Loss |
|:-------------:|:-----:|:------:|:---------------:|
| 0.9756        | 0.51  | 40000  | 0.9127          |
| 0.8876        | 1.01  | 80000  | 0.8221          |
| 0.818         | 1.52  | 120000 | 0.7786          |
| 0.7836        | 2.03  | 160000 | 0.7438          |
| 0.7672        | 2.54  | 200000 | 0.7165          |
| 0.734         | 3.04  | 240000 | 0.6948          |
| 0.7079        | 3.55  | 280000 | 0.6749          |
| 0.6987        | 4.06  | 320000 | 0.6598          |
| 0.6771        | 4.57  | 360000 | 0.6471          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu113
- Datasets 1.15.1
- Tokenizers 0.10.3
