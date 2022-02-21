---
language:
- uz
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M Uzbek CV8
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: uz
    metrics:
       - name: Test WER (with LM)
         type: wer
         value: 15.065
       - name: Test CER (with LM)
         type: cer
         value: 3.077
       - name: Test WER (no LM)
         type: wer
         value: 32.88
       - name: Test CER (no LM)
         type: cer
         value: 6.53
---

# XLS-R-300M Uzbek CV8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - UZ dataset.
It achieves the following results on the validation set:
- Loss: 0.3063
- Wer: 0.3852
- Cer: 0.0777

## Model description

For a description of the model architecture, see [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m)

The model vocabulary consists of the [Modern Latin alphabet for Uzbek](https://en.wikipedia.org/wiki/Uzbek_alphabet), with punctuation removed. 
Note that the characters <‘> and <’> do not count as punctuation, as <‘> modifies \<o\> and \<g\>, and <’> indicates the glottal stop or a long vowel.

The decoder uses a kenlm language model built on common_voice text.

## Intended uses & limitations

This model is expected to be of some utility for low-fidelity use cases such as:
- Draft video captions
- Indexing of recorded broadcasts

The model is not reliable enough to use as a substitute for live captions for accessibility purposes, and it should not be used in a manner that would infringe the privacy of any of the contributors to the Common Voice dataset nor any other speakers.

## Training and evaluation data

The 50% of the `train` common voice official split was used as training data. The 50% of the official `dev` split was used as validation data, and the full `test` set was used for final evaluation of the model without LM, while the model with LM was evaluated only on 500 examples from the `test` set.

The kenlm language model was compiled from the target sentences of the train + other dataset splits.

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 3.1401        | 3.25  | 500   | 3.1146          | 1.0    | 1.0    |
| 2.7484        | 6.49  | 1000  | 2.2842          | 1.0065 | 0.7069 |
| 1.0899        | 9.74  | 1500  | 0.5414          | 0.6125 | 0.1351 |
| 0.9465        | 12.99 | 2000  | 0.4566          | 0.5635 | 0.1223 |
| 0.8771        | 16.23 | 2500  | 0.4212          | 0.5366 | 0.1161 |
| 0.8346        | 19.48 | 3000  | 0.3994          | 0.5144 | 0.1102 |
| 0.8127        | 22.73 | 3500  | 0.3819          | 0.4944 | 0.1051 |
| 0.7833        | 25.97 | 4000  | 0.3705          | 0.4798 | 0.1011 |
| 0.7603        | 29.22 | 4500  | 0.3661          | 0.4704 | 0.0992 |
| 0.7424        | 32.47 | 5000  | 0.3529          | 0.4577 | 0.0957 |
| 0.7251        | 35.71 | 5500  | 0.3410          | 0.4473 | 0.0928 |
| 0.7106        | 38.96 | 6000  | 0.3401          | 0.4428 | 0.0919 |
| 0.7027        | 42.21 | 6500  | 0.3355          | 0.4353 | 0.0905 |
| 0.6927        | 45.45 | 7000  | 0.3308          | 0.4296 | 0.0885 |
| 0.6828        | 48.7  | 7500  | 0.3246          | 0.4204 | 0.0863 |
| 0.6706        | 51.95 | 8000  | 0.3250          | 0.4233 | 0.0868 |
| 0.6629        | 55.19 | 8500  | 0.3264          | 0.4159 | 0.0849 |
| 0.6556        | 58.44 | 9000  | 0.3213          | 0.4100 | 0.0835 |
| 0.6484        | 61.69 | 9500  | 0.3182          | 0.4124 | 0.0837 |
| 0.6407        | 64.93 | 10000 | 0.3171          | 0.4050 | 0.0825 |
| 0.6375        | 68.18 | 10500 | 0.3150          | 0.4039 | 0.0822 |
| 0.6363        | 71.43 | 11000 | 0.3129          | 0.3991 | 0.0810 |
| 0.6307        | 74.67 | 11500 | 0.3114          | 0.3986 | 0.0807 |
| 0.6232        | 77.92 | 12000 | 0.3103          | 0.3895 | 0.0790 |
| 0.6216        | 81.17 | 12500 | 0.3086          | 0.3891 | 0.0790 |
| 0.6174        | 84.41 | 13000 | 0.3082          | 0.3881 | 0.0785 |
| 0.6196        | 87.66 | 13500 | 0.3059          | 0.3875 | 0.0782 |
| 0.6174        | 90.91 | 14000 | 0.3084          | 0.3862 | 0.0780 |
| 0.6169        | 94.16 | 14500 | 0.3070          | 0.3860 | 0.0779 |
| 0.6166        | 97.4  | 15000 | 0.3066          | 0.3855 | 0.0778 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
