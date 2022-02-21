---

model-index:
- name: reformer-clm
---
## reformer-clm

This casual language model was trained from scratch on CNN/Dailymail dataset.
It achieves the following results on the evaluation set:
- Loss: 2.7783

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 500
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step   | Validation Loss |
|:-------------:|:-----:|:------:|:---------------:|
| 3.8321        | 1.0   | 18412  | 3.8074          |
| 3.4965        | 2.0   | 36824  | 3.4223          |
| 3.1927        | 3.0   | 55236  | 3.0815          |
| 3.046         | 4.0   | 73648  | 2.9270          |
| 2.9781        | 5.0   | 92060  | 2.8515          |
| 2.9398        | 6.0   | 110472 | 2.8082          |
| 2.9293        | 7.0   | 128884 | 2.7904          |
| 2.9212        | 8.0   | 147296 | 2.7817          |
| 2.9169        | 9.0   | 165708 | 2.7787          |
| 2.9197        | 10.0  | 184120 | 2.7783          |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.9.0
- Datasets 1.2.1
- Tokenizers 0.10.3
