---
language:
- dv
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- dv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Dhivehi
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: dv
    metrics:
       - name: Test WER
         type: wer
         value: 21.31
       - name: Test CER
         type: cer
         value: 3.82
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xls-r-300m-dv

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2855
- Wer: 0.2665

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 4.3386        | 0.66  | 400   | 1.1411          | 0.9432 |
| 0.6543        | 1.33  | 800   | 0.5099          | 0.6749 |
| 0.4646        | 1.99  | 1200  | 0.4133          | 0.5968 |
| 0.3748        | 2.65  | 1600  | 0.3534          | 0.5515 |
| 0.3323        | 3.32  | 2000  | 0.3635          | 0.5527 |
| 0.3269        | 3.98  | 2400  | 0.3587          | 0.5423 |
| 0.2984        | 4.64  | 2800  | 0.3340          | 0.5073 |
| 0.2841        | 5.31  | 3200  | 0.3279          | 0.5004 |
| 0.2664        | 5.97  | 3600  | 0.3114          | 0.4845 |
| 0.2397        | 6.63  | 4000  | 0.3174          | 0.4920 |
| 0.2332        | 7.3   | 4400  | 0.3110          | 0.4911 |
| 0.2304        | 7.96  | 4800  | 0.3123          | 0.4785 |
| 0.2134        | 8.62  | 5200  | 0.2984          | 0.4557 |
| 0.2066        | 9.29  | 5600  | 0.3013          | 0.4723 |
| 0.1951        | 9.95  | 6000  | 0.2934          | 0.4487 |
| 0.1806        | 10.61 | 6400  | 0.2802          | 0.4547 |
| 0.1727        | 11.28 | 6800  | 0.2842          | 0.4333 |
| 0.1666        | 11.94 | 7200  | 0.2873          | 0.4272 |
| 0.1562        | 12.6  | 7600  | 0.3042          | 0.4373 |
| 0.1483        | 13.27 | 8000  | 0.3122          | 0.4313 |
| 0.1465        | 13.93 | 8400  | 0.2760          | 0.4226 |
| 0.1335        | 14.59 | 8800  | 0.3112          | 0.4243 |
| 0.1293        | 15.26 | 9200  | 0.3002          | 0.4133 |
| 0.1264        | 15.92 | 9600  | 0.2985          | 0.4145 |
| 0.1179        | 16.58 | 10000 | 0.2925          | 0.4012 |
| 0.1171        | 17.25 | 10400 | 0.3127          | 0.4012 |
| 0.1141        | 17.91 | 10800 | 0.2980          | 0.3908 |
| 0.108         | 18.57 | 11200 | 0.3108          | 0.3951 |
| 0.1045        | 19.24 | 11600 | 0.3269          | 0.3908 |
| 0.1047        | 19.9  | 12000 | 0.2998          | 0.3868 |
| 0.0937        | 20.56 | 12400 | 0.2918          | 0.3875 |
| 0.0949        | 21.23 | 12800 | 0.2906          | 0.3657 |
| 0.0879        | 21.89 | 13200 | 0.2974          | 0.3731 |
| 0.0854        | 22.55 | 13600 | 0.2943          | 0.3711 |
| 0.0851        | 23.22 | 14000 | 0.2919          | 0.3580 |
| 0.0789        | 23.88 | 14400 | 0.2983          | 0.3560 |
| 0.0796        | 24.54 | 14800 | 0.3131          | 0.3544 |
| 0.0761        | 25.21 | 15200 | 0.2996          | 0.3616 |
| 0.0755        | 25.87 | 15600 | 0.2972          | 0.3506 |
| 0.0726        | 26.53 | 16000 | 0.2902          | 0.3474 |
| 0.0707        | 27.2  | 16400 | 0.3083          | 0.3480 |
| 0.0669        | 27.86 | 16800 | 0.3035          | 0.3330 |
| 0.0637        | 28.52 | 17200 | 0.2963          | 0.3370 |
| 0.0596        | 29.19 | 17600 | 0.2830          | 0.3326 |
| 0.0583        | 29.85 | 18000 | 0.2969          | 0.3287 |
| 0.0566        | 30.51 | 18400 | 0.3002          | 0.3480 |
| 0.0574        | 31.18 | 18800 | 0.2916          | 0.3296 |
| 0.0536        | 31.84 | 19200 | 0.2933          | 0.3225 |
| 0.0548        | 32.5  | 19600 | 0.2900          | 0.3179 |
| 0.0506        | 33.17 | 20000 | 0.3073          | 0.3225 |
| 0.0511        | 33.83 | 20400 | 0.2925          | 0.3275 |
| 0.0483        | 34.49 | 20800 | 0.2919          | 0.3245 |
| 0.0456        | 35.16 | 21200 | 0.2859          | 0.3105 |
| 0.0445        | 35.82 | 21600 | 0.2864          | 0.3080 |
| 0.0437        | 36.48 | 22000 | 0.2989          | 0.3084 |
| 0.04          | 37.15 | 22400 | 0.2887          | 0.3060 |
| 0.0406        | 37.81 | 22800 | 0.2870          | 0.3013 |
| 0.0397        | 38.47 | 23200 | 0.2793          | 0.3020 |
| 0.0383        | 39.14 | 23600 | 0.2955          | 0.2943 |
| 0.0345        | 39.8  | 24000 | 0.2813          | 0.2905 |
| 0.0331        | 40.46 | 24400 | 0.2845          | 0.2845 |
| 0.0338        | 41.13 | 24800 | 0.2832          | 0.2925 |
| 0.0333        | 41.79 | 25200 | 0.2889          | 0.2849 |
| 0.0325        | 42.45 | 25600 | 0.2808          | 0.2847 |
| 0.0314        | 43.12 | 26000 | 0.2867          | 0.2801 |
| 0.0288        | 43.78 | 26400 | 0.2865          | 0.2834 |
| 0.0291        | 44.44 | 26800 | 0.2863          | 0.2806 |
| 0.0269        | 45.11 | 27200 | 0.2941          | 0.2736 |
| 0.0275        | 45.77 | 27600 | 0.2897          | 0.2736 |
| 0.0271        | 46.43 | 28000 | 0.2857          | 0.2695 |
| 0.0251        | 47.1  | 28400 | 0.2881          | 0.2702 |
| 0.0243        | 47.76 | 28800 | 0.2901          | 0.2684 |
| 0.0244        | 48.42 | 29200 | 0.2849          | 0.2679 |
| 0.0232        | 49.09 | 29600 | 0.2849          | 0.2677 |
| 0.0224        | 49.75 | 30000 | 0.2855          | 0.2665 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
