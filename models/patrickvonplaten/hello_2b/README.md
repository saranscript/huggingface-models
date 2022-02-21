---
language:
- tr
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: hello_2b
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hello_2b

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-2b](https://huggingface.co/facebook/wav2vec2-xls-r-2b) on the COMMON_VOICE - TR dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2725
- Wer: 0.9531

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- distributed_type: multi-GPU
- num_devices: 2
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- total_eval_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.1646        | 0.92  | 100  | 3.2106          | 1.0    |
| 0.368         | 1.85  | 200  | 2.9963          | 1.0    |
| 0.2252        | 2.77  | 300  | 2.8078          | 0.9999 |
| 0.1546        | 3.7   | 400  | 2.3458          | 0.9996 |
| 0.1468        | 4.63  | 500  | 2.0086          | 0.9986 |
| 0.1261        | 5.55  | 600  | 1.8269          | 0.9985 |
| 0.1206        | 6.48  | 700  | 1.7347          | 0.9956 |
| 0.1959        | 7.4   | 800  | 1.6819          | 0.9955 |
| 0.0502        | 8.33  | 900  | 1.6809          | 0.9965 |
| 0.0811        | 9.26  | 1000 | 1.6674          | 0.9916 |
| 0.0534        | 10.18 | 1100 | 1.5719          | 0.9898 |
| 0.0402        | 11.11 | 1200 | 1.4620          | 0.9821 |
| 0.057         | 12.04 | 1300 | 1.3015          | 0.9554 |
| 0.0385        | 12.96 | 1400 | 1.3798          | 0.9600 |
| 0.0422        | 13.88 | 1500 | 1.3538          | 0.9699 |
| 0.014         | 14.81 | 1600 | 1.2507          | 0.9443 |
| 0.0232        | 15.74 | 1700 | 1.3318          | 0.9465 |
| 0.0554        | 16.66 | 1800 | 1.2784          | 0.9462 |
| 0.0316        | 17.59 | 1900 | 1.2503          | 0.9481 |
| 0.0524        | 18.51 | 2000 | 1.3920          | 0.9604 |
| 0.0142        | 19.44 | 2100 | 1.4224          | 0.9698 |
| 0.0288        | 20.37 | 2200 | 1.3475          | 0.9635 |
| 0.0106        | 21.29 | 2300 | 1.2232          | 0.9264 |
| 0.0396        | 22.22 | 2400 | 1.3323          | 0.9615 |
| 0.0349        | 23.15 | 2500 | 1.2741          | 0.9587 |
| 0.0121        | 24.07 | 2600 | 1.2671          | 0.9586 |
| 0.0224        | 24.99 | 2700 | 1.3001          | 0.9611 |
| 0.0449        | 25.92 | 2800 | 1.2777          | 0.9572 |
| 0.0186        | 26.85 | 2900 | 1.2766          | 0.9607 |
| 0.0365        | 27.77 | 3000 | 1.2935          | 0.9598 |
| 0.0105        | 28.7  | 3100 | 1.2761          | 0.9588 |
| 0.021         | 29.63 | 3200 | 1.2686          | 0.9528 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
