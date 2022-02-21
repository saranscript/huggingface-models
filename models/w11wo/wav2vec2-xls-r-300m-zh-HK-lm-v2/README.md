---
language: zh-HK
license: apache-2.0
tags:
  - automatic-speech-recognition
  - generated_from_trainer
  - robust-speech-event
datasets:
  - common_voice
model-index:
  - name: Wav2Vec2 XLS-R 300M Cantonese (zh-HK) LM
    results:
      - task:
          name: Automatic Speech Recognition
          type: automatic-speech-recognition
        dataset:
          name: Common Voice
          type: common_voice
          args: zh-HK
        metrics:
          - name: Test CER
            type: cer
            value: 24.09
      - task:
          name: Automatic Speech Recognition
          type: automatic-speech-recognition
        dataset:
          name: Common Voice 7
          type: mozilla-foundation/common_voice_7_0
          args: zh-HK
        metrics:
          - name: Test CER
            type: cer
            value: 23.10
      - task:
          name: Automatic Speech Recognition
          type: automatic-speech-recognition
        dataset:
          name: Common Voice 8
          type: mozilla-foundation/common_voice_8_0
          args: zh-HK
        metrics:
          - name: Test CER
            type: cer
            value: 23.02
      - task:
          name: Automatic Speech Recognition
          type: automatic-speech-recognition
        dataset:
          name: Robust Speech Event - Dev Data
          type: speech-recognition-community-v2/dev_data
          args: zh-HK
        metrics:
          - name: Test CER
            type: cer
            value: 56.86
---

# Wav2Vec2 XLS-R 300M Cantonese (zh-HK) LM

Wav2Vec2 XLS-R 300M Cantonese (zh-HK) LM is an automatic speech recognition model based on the [XLS-R](https://arxiv.org/abs/2111.09296) architecture. This model is a fine-tuned version of [Wav2Vec2-XLS-R-300M](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the `zh-HK` subset of the [Common Voice](https://huggingface.co/datasets/common_voice) dataset. A 5-gram Language model, trained on multiple [PyCantonese](https://pycantonese.org/data.html) corpora, was then subsequently added to this model.

This model was trained using HuggingFace's PyTorch framework and is part of the [Robust Speech Challenge Event](https://discuss.huggingface.co/t/open-to-the-community-robust-speech-recognition-challenge/13614) organized by HuggingFace. All training was done on a Tesla V100, sponsored by OVH.

All necessary scripts used for training could be found in the [Files and versions](https://huggingface.co/w11wo/wav2vec2-xls-r-300m-zh-HK-lm-v2/tree/main) tab, as well as the [Training metrics](https://huggingface.co/w11wo/wav2vec2-xls-r-300m-zh-HK-lm-v2/tensorboard) logged via Tensorboard.

As for the N-gram language model training, we followed the [blog post tutorial](https://huggingface.co/blog/wav2vec2-with-ngram) provided by HuggingFace.

## Model

| Model                             | #params | Arch. | Training/Validation data (text) |
| --------------------------------- | ------- | ----- | ------------------------------- |
| `wav2vec2-xls-r-300m-zh-HK-lm-v2` | 300M    | XLS-R | `Common Voice zh-HK` Dataset    |

## Evaluation Results

The model achieves the following results on evaluation without a language model:

| Dataset                          | CER    |
| -------------------------------- | ------ |
| `Common Voice`                   | 31.73% |
| `Common Voice 7`                 | 23.11% |
| `Common Voice 8`                 | 23.02% |
| `Robust Speech Event - Dev Data` | 56.60% |

With the addition of the language model, it achieves the following results:

| Dataset                          | CER    |
| -------------------------------- | ------ |
| `Common Voice`                   | 24.09% |
| `Common Voice 7`                 | 23.10% |
| `Common Voice 8`                 | 23.02% |
| `Robust Speech Event - Dev Data` | 56.86% |

## Training procedure

The training process did not involve the addition of a language model. The following results were simply lifted from the original automatic speech recognition [model training](https://huggingface.co/w11wo/wav2vec2-xls-r-300m-zh-HK-v2).

### Training hyperparameters

The following hyperparameters were used during training:

- `learning_rate`: 0.0001
- `train_batch_size`: 8
- `eval_batch_size`: 8
- `seed`: 42
- `gradient_accumulation_steps`: 4
- `total_train_batch_size`: 32
- `optimizer`: Adam with `betas=(0.9, 0.999)` and `epsilon=1e-08`
- `lr_scheduler_type`: linear
- `lr_scheduler_warmup_steps`: 2000
- `num_epochs`: 100.0
- `mixed_precision_training`: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss |  Wer   |  Cer   |
| :-----------: | :---: | :---: | :-------------: | :----: | :----: |
|    69.8341    | 1.34  |  500  |     80.0722     |  1.0   |  1.0   |
|    6.6418     | 2.68  | 1000  |     6.6346      |  1.0   |  1.0   |
|    6.2419     | 4.02  | 1500  |     6.2909      |  1.0   |  1.0   |
|    6.0813     | 5.36  | 2000  |     6.1150      |  1.0   |  1.0   |
|    5.9677     |  6.7  | 2500  |     6.0301      | 1.1386 | 1.0028 |
|    5.9296     | 8.04  | 3000  |     5.8975      | 1.2113 | 1.0058 |
|    5.6434     | 9.38  | 3500  |     5.5404      | 2.1624 | 1.0171 |
|    5.1974     | 10.72 | 4000  |     4.5440      | 2.1702 | 0.9366 |
|    4.3601     | 12.06 | 4500  |     3.3839      | 2.2464 | 0.8998 |
|    3.9321     | 13.4  | 5000  |     2.8785      | 2.3097 | 0.8400 |
|    3.6462     | 14.74 | 5500  |     2.5108      | 1.9623 | 0.6663 |
|    3.5156     | 16.09 | 6000  |     2.2790      | 1.6479 | 0.5706 |
|     3.32      | 17.43 | 6500  |     2.1450      | 1.8337 | 0.6244 |
|    3.1918     | 18.77 | 7000  |     1.8536      | 1.9394 | 0.6017 |
|    3.1139     | 20.11 | 7500  |     1.7205      | 1.9112 | 0.5638 |
|    2.8995     | 21.45 | 8000  |     1.5478      | 1.0624 | 0.3250 |
|    2.7572     | 22.79 | 8500  |     1.4068      | 1.1412 | 0.3367 |
|    2.6881     | 24.13 | 9000  |     1.3312      | 2.0100 | 0.5683 |
|    2.5993     | 25.47 | 9500  |     1.2553      | 2.0039 | 0.6450 |
|    2.5304     | 26.81 | 10000 |     1.2422      | 2.0394 | 0.5789 |
|    2.4352     | 28.15 | 10500 |     1.1582      | 1.9970 | 0.5507 |
|    2.3795     | 29.49 | 11000 |     1.1160      | 1.8255 | 0.4844 |
|    2.3287     | 30.83 | 11500 |     1.0775      | 1.4123 | 0.3780 |
|    2.2622     | 32.17 | 12000 |     1.0704      | 1.7445 | 0.4894 |
|    2.2225     | 33.51 | 12500 |     1.0272      | 1.7237 | 0.5058 |
|    2.1843     | 34.85 | 13000 |     0.9756      | 1.8042 | 0.5028 |
|      2.1      | 36.19 | 13500 |     0.9527      | 1.8909 | 0.6055 |
|    2.0741     | 37.53 | 14000 |     0.9418      | 1.9026 | 0.5880 |
|    2.0179     | 38.87 | 14500 |     0.9363      | 1.7977 | 0.5246 |
|    2.0615     | 40.21 | 15000 |     0.9635      | 1.8112 | 0.5599 |
|    1.9448     | 41.55 | 15500 |     0.9249      | 1.7250 | 0.4914 |
|    1.8966     | 42.89 | 16000 |     0.9023      | 1.5829 | 0.4319 |
|    1.8662     | 44.24 | 16500 |     0.9002      | 1.4833 | 0.4230 |
|    1.8136     | 45.58 | 17000 |     0.9076      | 1.1828 | 0.2987 |
|    1.7908     | 46.92 | 17500 |     0.8774      | 1.5773 | 0.4258 |
|    1.7354     | 48.26 | 18000 |     0.8727      | 1.5037 | 0.4024 |
|    1.6739     | 49.6  | 18500 |     0.8636      | 1.1239 | 0.2789 |
|    1.6457     | 50.94 | 19000 |     0.8516      | 1.2269 | 0.3104 |
|    1.5847     | 52.28 | 19500 |     0.8399      | 1.3309 | 0.3360 |
|    1.5971     | 53.62 | 20000 |     0.8441      | 1.3153 | 0.3335 |
|     1.602     | 54.96 | 20500 |     0.8590      | 1.2932 | 0.3433 |
|    1.5063     | 56.3  | 21000 |     0.8334      | 1.1312 | 0.2875 |
|    1.4631     | 57.64 | 21500 |     0.8474      | 1.1698 | 0.2999 |
|    1.4997     | 58.98 | 22000 |     0.8638      | 1.4279 | 0.3854 |
|    1.4301     | 60.32 | 22500 |     0.8550      | 1.2737 | 0.3300 |
|    1.3798     | 61.66 | 23000 |     0.8266      | 1.1802 | 0.2934 |
|    1.3454     | 63.0  | 23500 |     0.8235      | 1.3816 | 0.3711 |
|    1.3678     | 64.34 | 24000 |     0.8550      | 1.6427 | 0.5035 |
|    1.3761     | 65.68 | 24500 |     0.8510      | 1.6709 | 0.4907 |
|    1.2668     | 67.02 | 25000 |     0.8515      | 1.5842 | 0.4505 |
|    1.2835     | 68.36 | 25500 |     0.8283      | 1.5353 | 0.4221 |
|    1.2961     | 69.7  | 26000 |     0.8339      | 1.5743 | 0.4369 |
|    1.2656     | 71.05 | 26500 |     0.8331      | 1.5331 | 0.4217 |
|    1.2556     | 72.39 | 27000 |     0.8242      | 1.4708 | 0.4109 |
|    1.2043     | 73.73 | 27500 |     0.8245      | 1.4469 | 0.4031 |
|    1.2722     | 75.07 | 28000 |     0.8202      | 1.4924 | 0.4096 |
|     1.202     | 76.41 | 28500 |     0.8290      | 1.3807 | 0.3719 |
|    1.1679     | 77.75 | 29000 |     0.8195      | 1.4097 | 0.3749 |
|    1.1967     | 79.09 | 29500 |     0.8059      | 1.2074 | 0.3077 |
|    1.1241     | 80.43 | 30000 |     0.8137      | 1.2451 | 0.3270 |
|    1.1414     | 81.77 | 30500 |     0.8117      | 1.2031 | 0.3121 |
|     1.132     | 83.11 | 31000 |     0.8234      | 1.4266 | 0.3901 |
|    1.0982     | 84.45 | 31500 |     0.8064      | 1.3712 | 0.3607 |
|    1.0797     | 85.79 | 32000 |     0.8167      | 1.3356 | 0.3562 |
|    1.0119     | 87.13 | 32500 |     0.8215      | 1.2754 | 0.3268 |
|    1.0216     | 88.47 | 33000 |     0.8163      | 1.2512 | 0.3184 |
|    1.0375     | 89.81 | 33500 |     0.8137      | 1.2685 | 0.3290 |
|    0.9794     | 91.15 | 34000 |     0.8220      | 1.2724 | 0.3255 |
|    1.0207     | 92.49 | 34500 |     0.8165      | 1.2906 | 0.3361 |
|    1.0169     | 93.83 | 35000 |     0.8153      | 1.2819 | 0.3305 |
|    1.0127     | 95.17 | 35500 |     0.8187      | 1.2832 | 0.3252 |
|    0.9978     | 96.51 | 36000 |     0.8111      | 1.2612 | 0.3210 |
|    0.9923     | 97.85 | 36500 |     0.8076      | 1.2278 | 0.3122 |
|    1.0451     | 99.2  | 37000 |     0.8086      | 1.2451 | 0.3156 |

## Disclaimer

Do consider the biases which came from pre-training datasets that may be carried over into the results of this model.

## Authors

Wav2Vec2 XLS-R 300M Cantonese (zh-HK) LM was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on OVH Cloud.

## Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
