---
language:
- sr
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
- xlsr-fine-tuning-week
datasets:
- mozilla-foundation/common_voice_8_0
- name: Serbian comodoro Wav2Vec2 XLSR 300M CV8
  results:
  - task:
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sr
    metrics:
       - name: Test WER
         type: wer
         value: 48.5
       - name: Test CER
         type: cer
         value: 18.4
---

# Serbian wav2vec2-xls-r-300m-sr-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.7302
- Wer: 0.4825
- Cer: 0.1847

Evaluation on mozilla-foundation/common_voice_8_0 gave the following results:

- WER: 0.48530097993467103
- CER: 0.18413288165227845

Evaluation on  speech-recognition-community-v2/dev_data gave the following results:

- WER: 0.9718373107518604
- CER: 0.8302740620263108

The model can be evaluated using the attached `eval.py` script:
```
python eval.py --model_id comodoro/wav2vec2-xls-r-300m-sr-cv8 --dataset mozilla-foundation/common-voice_8_0 --split test --config sr
```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 300
- num_epochs: 800
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 5.6536        | 15.0  | 1200  | 2.9744          | 1.0    | 1.0    |
| 2.7935        | 30.0  | 2400  | 1.6613          | 0.8998 | 0.4670 |
| 1.6538        | 45.0  | 3600  | 0.9248          | 0.6918 | 0.2699 |
| 1.2446        | 60.0  | 4800  | 0.9151          | 0.6452 | 0.2398 |
| 1.0766        | 75.0  | 6000  | 0.9110          | 0.5995 | 0.2207 |
| 0.9548        | 90.0  | 7200  | 1.0273          | 0.5921 | 0.2149 |
| 0.8919        | 105.0 | 8400  | 0.9929          | 0.5646 | 0.2117 |
| 0.8185        | 120.0 | 9600  | 1.0850          | 0.5483 | 0.2069 |
| 0.7692        | 135.0 | 10800 | 1.1001          | 0.5394 | 0.2055 |
| 0.7249        | 150.0 | 12000 | 1.1018          | 0.5380 | 0.1958 |
| 0.6786        | 165.0 | 13200 | 1.1344          | 0.5114 | 0.1941 |
| 0.6432        | 180.0 | 14400 | 1.1516          | 0.5054 | 0.1905 |
| 0.6009        | 195.0 | 15600 | 1.3149          | 0.5324 | 0.1991 |
| 0.5773        | 210.0 | 16800 | 1.2468          | 0.5124 | 0.1903 |
| 0.559         | 225.0 | 18000 | 1.2186          | 0.4956 | 0.1922 |
| 0.5298        | 240.0 | 19200 | 1.4483          | 0.5333 | 0.2085 |
| 0.5136        | 255.0 | 20400 | 1.2871          | 0.4802 | 0.1846 |
| 0.4824        | 270.0 | 21600 | 1.2891          | 0.4974 | 0.1885 |
| 0.4669        | 285.0 | 22800 | 1.3283          | 0.4942 | 0.1878 |
| 0.4511        | 300.0 | 24000 | 1.4502          | 0.5002 | 0.1994 |
| 0.4337        | 315.0 | 25200 | 1.4714          | 0.5035 | 0.1911 |
| 0.4221        | 330.0 | 26400 | 1.4971          | 0.5124 | 0.1962 |
| 0.3994        | 345.0 | 27600 | 1.4473          | 0.5007 | 0.1920 |
| 0.3892        | 360.0 | 28800 | 1.3904          | 0.4937 | 0.1887 |
| 0.373         | 375.0 | 30000 | 1.4971          | 0.4946 | 0.1902 |
| 0.3657        | 390.0 | 31200 | 1.4208          | 0.4900 | 0.1821 |
| 0.3559        | 405.0 | 32400 | 1.4648          | 0.4895 | 0.1835 |
| 0.3476        | 420.0 | 33600 | 1.4848          | 0.4946 | 0.1829 |
| 0.3276        | 435.0 | 34800 | 1.5597          | 0.4979 | 0.1873 |
| 0.3193        | 450.0 | 36000 | 1.7329          | 0.5040 | 0.1980 |
| 0.3078        | 465.0 | 37200 | 1.6379          | 0.4937 | 0.1882 |
| 0.3058        | 480.0 | 38400 | 1.5878          | 0.4942 | 0.1921 |
| 0.2987        | 495.0 | 39600 | 1.5590          | 0.4811 | 0.1846 |
| 0.2931        | 510.0 | 40800 | 1.6001          | 0.4825 | 0.1849 |
| 0.276         | 525.0 | 42000 | 1.7388          | 0.4942 | 0.1918 |
| 0.2702        | 540.0 | 43200 | 1.7037          | 0.4839 | 0.1866 |
| 0.2619        | 555.0 | 44400 | 1.6704          | 0.4755 | 0.1840 |
| 0.262         | 570.0 | 45600 | 1.6042          | 0.4751 | 0.1865 |
| 0.2528        | 585.0 | 46800 | 1.6402          | 0.4821 | 0.1865 |
| 0.2442        | 600.0 | 48000 | 1.6693          | 0.4886 | 0.1862 |
| 0.244         | 615.0 | 49200 | 1.6203          | 0.4765 | 0.1792 |
| 0.2388        | 630.0 | 50400 | 1.6829          | 0.4830 | 0.1828 |
| 0.2362        | 645.0 | 51600 | 1.8100          | 0.4928 | 0.1888 |
| 0.2224        | 660.0 | 52800 | 1.7746          | 0.4932 | 0.1899 |
| 0.2218        | 675.0 | 54000 | 1.7752          | 0.4946 | 0.1901 |
| 0.2201        | 690.0 | 55200 | 1.6775          | 0.4788 | 0.1844 |
| 0.2147        | 705.0 | 56400 | 1.7085          | 0.4844 | 0.1851 |
| 0.2103        | 720.0 | 57600 | 1.7624          | 0.4848 | 0.1864 |
| 0.2101        | 735.0 | 58800 | 1.7213          | 0.4783 | 0.1835 |
| 0.1983        | 750.0 | 60000 | 1.7452          | 0.4848 | 0.1856 |
| 0.2015        | 765.0 | 61200 | 1.7525          | 0.4872 | 0.1869 |
| 0.1969        | 780.0 | 62400 | 1.7443          | 0.4844 | 0.1852 |
| 0.2043        | 795.0 | 63600 | 1.7302          | 0.4825 | 0.1847 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
