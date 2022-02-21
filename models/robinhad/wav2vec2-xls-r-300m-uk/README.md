---
language:
- uk
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-uk
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice uk
      type: common_voice
      args: uk
    metrics:
       - name: Test WER
         type: wer
         value: 27.99
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-uk

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.  
Notebook for training is located in this repository: [https://github.com/robinhad/wav2vec2-xls-r-ukrainian](https://github.com/robinhad/wav2vec2-xls-r-ukrainian).  
It achieves the following results on the evaluation set:
- Loss: 0.4165
- Wer: 0.2799
- Cer: 0.0601

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 20
- total_train_batch_size: 160
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 500
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Cer    | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:------:|:---------------:|:------:|
| 4.3982        | 9.3    | 400   | 0.1437 | 0.5218          | 0.6507 |
| 0.229         | 18.6   | 800   | 0.0848 | 0.3679          | 0.4048 |
| 0.1054        | 27.9   | 1200  | 0.0778 | 0.3813          | 0.3670 |
| 0.0784        | 37.21  | 1600  | 0.0747 | 0.3839          | 0.3550 |
| 0.066         | 46.51  | 2000  | 0.0736 | 0.3970          | 0.3443 |
| 0.0603        | 55.8   | 2400  | 0.0722 | 0.3702          | 0.3393 |
| 0.0539        | 65.11  | 2800  | 0.0724 | 0.3762          | 0.3388 |
| 0.0497        | 74.41  | 3200  | 0.0713 | 0.3623          | 0.3414 |
| 0.0432        | 83.71  | 3600  | 0.0725 | 0.3847          | 0.3346 |
| 0.0438        | 93.02  | 4000  | 0.0750 | 0.4058          | 0.3393 |
| 0.0413        | 102.32 | 4400  | 0.0727 | 0.3957          | 0.3363 |
| 0.039         | 111.62 | 4800  | 0.0718 | 0.3865          | 0.3330 |
| 0.0356        | 120.92 | 5200  | 0.0711 | 0.3860          | 0.3319 |
| 0.0336        | 130.23 | 5600  | 0.0700 | 0.3902          | 0.3242 |
| 0.034         | 139.53 | 6000  | 0.0732 | 0.3930          | 0.3337 |
| 0.0273        | 148.83 | 6400  | 0.0748 | 0.3912          | 0.3375 |
| 0.027         | 158.14 | 6800  | 0.0752 | 0.4266          | 0.3434 |
| 0.028         | 167.44 | 7200  | 0.0708 | 0.3895          | 0.3227 |
| 0.0241        | 176.73 | 7600  | 0.0727 | 0.3967          | 0.3294 |
| 0.0241        | 186.05 | 8000  | 0.0712 | 0.4058          | 0.3255 |
| 0.0209        | 195.34 | 8400  | 0.0702 | 0.4102          | 0.3233 |
| 0.0206        | 204.64 | 8800  | 0.0699 | 0.4075          | 0.3194 |
| 0.0172        | 213.94 | 9200  | 0.0695 | 0.4222          | 0.3191 |
| 0.0166        | 223.25 | 9600  | 0.0678 | 0.3860          | 0.3135 |
| 0.0156        | 232.55 | 10000 | 0.0677 | 0.4035          | 0.3117 |
| 0.0149        | 241.85 | 10400 | 0.0677 | 0.3951          | 0.3087 |
| 0.0142        | 251.16 | 10800 | 0.0674 | 0.3972          | 0.3097 |
| 0.0134        | 260.46 | 11200 | 0.0675 | 0.4069          | 0.3111 |
| 0.0116        | 269.76 | 11600 | 0.0697 | 0.4189          | 0.3161 |
| 0.0119        | 279.07 | 12000 | 0.0648 | 0.3902          | 0.3008 |
| 0.0098        | 288.37 | 12400 | 0.0652 | 0.4095          | 0.3002 |
| 0.0091        | 297.67 | 12800 | 0.0644 | 0.3892          | 0.2990 |
| 0.0094        | 306.96 | 13200 | 0.0647 | 0.4026          | 0.2983 |
| 0.0081        | 316.28 | 13600 | 0.0646 | 0.4303          | 0.2978 |
| 0.0079        | 325.57 | 14000 | 0.0643 | 0.4044          | 0.2980 |
| 0.0072        | 334.87 | 14400 | 0.0655 | 0.3828          | 0.2999 |
| 0.0081        | 344.18 | 14800 | 0.0668 | 0.4108          | 0.3046 |
| 0.0088        | 353.48 | 15200 | 0.0654 | 0.4019          | 0.2993 |
| 0.0088        | 362.78 | 15600 | 0.0681 | 0.4073          | 0.3091 |
| 0.0079        | 372.09 | 16000 | 0.0667 | 0.4204          | 0.3055 |
| 0.0072        | 381.39 | 16400 | 0.0656 | 0.4030          | 0.3028 |
| 0.0073        | 390.69 | 16800 | 0.0677 | 0.4032          | 0.3081 |
| 0.0069        | 399.99 | 17200 | 0.0669 | 0.4130          | 0.3021 |
| 0.0063        | 409.3  | 17600 | 0.0651 | 0.4072          | 0.2979 |
| 0.0059        | 418.6  | 18000 | 0.0640 | 0.4110          | 0.2969 |
| 0.0056        | 427.9  | 18400 | 0.0647 | 0.4229          | 0.2995 |
| 0.005         | 437.21 | 18800 | 0.0624 | 0.4118          | 0.2885 |
| 0.0046        | 446.51 | 19200 | 0.0615 | 0.4111          | 0.2841 |
| 0.0043        | 455.8  | 19600 | 0.0616 | 0.4071          | 0.2850 |
| 0.0038        | 465.11 | 20000 | 0.0624 | 0.4268          | 0.2867 |
| 0.0035        | 474.41 | 20400 | 0.0605 | 0.4117          | 0.2820 |
| 0.0035        | 483.71 | 20800 | 0.0602 | 0.4155          | 0.2819 |
| 0.0034        | 493.02 | 21200 | 0.0601 | 0.4165          | 0.2799 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.0
- Datasets 1.16.1
- Tokenizers 0.10.3
