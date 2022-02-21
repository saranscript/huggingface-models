---
language:
- ug
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- ug
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M Uyghur CV7
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: ug
    metrics:
       - name: Test WER
         type: wer
         value: 25.845
       - name: Test CER
         type: cer
         value: 4.795
---

# XLS-R-300M Uyghur CV7

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - UG dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1772
- Wer: 0.2589

## Model description

For a description of the model architecture, see [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m)

The model vocabulary consists of the alphabetic characters of the [Perso-Arabic script for the Uyghur language](https://omniglot.com/writing/uyghur.htm), with punctuation removed.

## Intended uses & limitations

This model is expected to be of some utility for low-fidelity use cases such as:
- Draft video captions
- Indexing of recorded broadcasts

The model is not reliable enough to use as a substitute for live captions for accessibility purposes, and it should not be used in a manner that would infringe the privacy of any of the contributors to the Common Voice dataset nor any other speakers.

## Training and evaluation data

The combination of `train` and `dev` of common voice official splits were used as training data. The official `test` split was used as validation data as well as for final evaluation.

## Training procedure

The featurization layers of the XLS-R model are frozen while tuning a final CTC/LM layer on the Uyghur CV7 example sentences. A ramped learning rate is used with an initial warmup phase of 2000 steps, a max of 0.0001, and cooling back towards 0 for the remainder of the 18500 steps (100 epochs).

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.3043        | 2.73  | 500   | 3.2415          | 1.0    |
| 3.0482        | 5.46  | 1000  | 2.9591          | 1.0    |
| 1.4767        | 8.2   | 1500  | 0.4779          | 0.5777 |
| 1.3152        | 10.93 | 2000  | 0.3697          | 0.4938 |
| 1.2246        | 13.66 | 2500  | 0.3084          | 0.4459 |
| 1.1781        | 16.39 | 3000  | 0.2842          | 0.4154 |
| 1.1351        | 19.13 | 3500  | 0.2615          | 0.3929 |
| 1.1052        | 21.86 | 4000  | 0.2462          | 0.3747 |
| 1.0711        | 24.59 | 4500  | 0.2366          | 0.3652 |
| 1.035         | 27.32 | 5000  | 0.2268          | 0.3557 |
| 1.0277        | 30.05 | 5500  | 0.2243          | 0.3450 |
| 1.002         | 32.79 | 6000  | 0.2204          | 0.3389 |
| 0.9837        | 35.52 | 6500  | 0.2156          | 0.3349 |
| 0.9773        | 38.25 | 7000  | 0.2127          | 0.3289 |
| 0.9807        | 40.98 | 7500  | 0.2142          | 0.3274 |
| 0.9582        | 43.72 | 8000  | 0.2004          | 0.3142 |
| 0.9548        | 46.45 | 8500  | 0.2022          | 0.3050 |
| 0.9251        | 49.18 | 9000  | 0.2019          | 0.3035 |
| 0.9103        | 51.91 | 9500  | 0.1964          | 0.3021 |
| 0.915         | 54.64 | 10000 | 0.1970          | 0.3032 |
| 0.8962        | 57.38 | 10500 | 0.2007          | 0.3046 |
| 0.8729        | 60.11 | 11000 | 0.1967          | 0.2942 |
| 0.8744        | 62.84 | 11500 | 0.1952          | 0.2885 |
| 0.874         | 65.57 | 12000 | 0.1894          | 0.2895 |
| 0.8457        | 68.31 | 12500 | 0.1895          | 0.2828 |
| 0.8519        | 71.04 | 13000 | 0.1912          | 0.2875 |
| 0.8301        | 73.77 | 13500 | 0.1878          | 0.2760 |
| 0.8226        | 76.5  | 14000 | 0.1808          | 0.2701 |
| 0.8071        | 79.23 | 14500 | 0.1849          | 0.2741 |
| 0.7999        | 81.97 | 15000 | 0.1808          | 0.2717 |
| 0.7947        | 84.7  | 15500 | 0.1821          | 0.2716 |
| 0.7783        | 87.43 | 16000 | 0.1824          | 0.2661 |
| 0.7729        | 90.16 | 16500 | 0.1773          | 0.2639 |
| 0.7759        | 92.9  | 17000 | 0.1767          | 0.2629 |
| 0.7713        | 95.63 | 17500 | 0.1780          | 0.2621 |
| 0.7628        | 98.36 | 18000 | 0.1773          | 0.2594 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
