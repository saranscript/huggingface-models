---
language:
- ne
license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- openslr
model-index:
- name: wav2vec2-large-xlsr-300m-nepali
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: openslr 
      type: openslr
      args: ne
    metrics:
       - name: Test WER
         type: wer
         value: 25.02 
---
# wav2vec2-large-xlsr-300m-nepali

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m)

The dataset used to train are :

1. [OpenSLR-54 Corpus](https://openslr.org/54/)
2. External Data 

For evaluation on publicly available datasets, can use [OpenSLR-43 corpus - Model is not trained on this data](http://www.openslr.org/43) which is also available on [HuggingFace as train-set](https://huggingface.co/datasets/openslr/viewer/SLR43/train) where it achieves **27% WER and 8.3% CER** with 5 gram language model.

Script to Evaluate the Model on OpenSLR-43 train set :

	python3 eval.py --model_id prajin/wav2vec2-large-xlsr-300m-nepali --dataset openslr --config SLR43  --split train --log_outputs



Below evaluation result is the evaluation on separated 10000 samples from total training dataset.

It achieves the following results on the evaluation set Without using Language Model :
- Loss: 0.2625
- Wer: 0.3426

With Language model ( 5 gram ) 
- Wer: 0.2502



## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 6e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.3468        | 0.04  | 400   | 0.2624          | 0.3479 |
| 0.2792        | 0.08  | 800   | 0.2696          | 0.3490 |
| 0.245         | 0.12  | 1200  | 0.2751          | 0.3502 |
| 0.2453        | 0.16  | 1600  | 0.2754          | 0.3523 |
| 0.2332        | 0.2   | 2000  | 0.2779          | 0.3517 |
| 0.2321        | 0.24  | 2400  | 0.2775          | 0.3528 |
| 0.2708        | 0.28  | 2800  | 0.2764          | 0.3533 |
| 0.2709        | 0.32  | 3200  | 0.2723          | 0.3544 |
| 0.2715        | 0.36  | 3600  | 0.2739          | 0.3545 |
| 0.2732        | 0.4   | 4000  | 0.2707          | 0.3498 |
| 0.2643        | 0.44  | 4400  | 0.2696          | 0.3499 |
| 0.2682        | 0.47  | 4800  | 0.2672          | 0.3492 |
| 0.2687        | 0.51  | 5200  | 0.2644          | 0.3474 |
| 0.269         | 0.55  | 5600  | 0.2619          | 0.3502 |
| 0.2675        | 0.59  | 6000  | 0.2606          | 0.3477 |
| 0.2656        | 0.63  | 6400  | 0.2597          | 0.3463 |
| 0.2667        | 0.67  | 6800  | 0.2607          | 0.3458 |
| 0.2639        | 0.71  | 7200  | 0.2601          | 0.3480 |
| 0.2631        | 0.75  | 7600  | 0.2582          | 0.3447 |
| 0.2589        | 0.79  | 8000  | 0.2577          | 0.3438 |
| 0.2554        | 0.83  | 8400  | 0.2557          | 0.3439 |
| 0.2687        | 0.87  | 8800  | 0.2546          | 0.3438 |
| 0.2574        | 0.91  | 9200  | 0.2537          | 0.3434 |
| 0.2623        | 0.95  | 9600  | 0.2530          | 0.3433 |
| 0.2675        | 0.99  | 10000 | 0.2530          | 0.3426 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
