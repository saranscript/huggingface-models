---
language:
- it
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300m - Italian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: it
    metrics:
       - name: Test WER
         type: wer
         value: 19.44
       - name: Test CER
         type: cer
         value: 4.47
       - name: Test WER (+LM)
         type: wer
         value: 14.08
       - name: Test CER (+LM)
         type: cer
         value: 3.67
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: it
    metrics:
       - name: Test WER
         type: wer
         value: 31.01
       - name: Test CER
         type: cer
         value: 9.27
       - name: Test WER (+LM)
         type: wer
         value: 22.09
       - name: Test CER (+LM)
         type: cer
         value: 7.90
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-italian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - IT dataset.
It achieves the following results on the evaluation set:
- Loss: inf
- Wer: 0.1710

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
- train_batch_size: 64
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 5.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| No log        | 0.04  | 100   | inf             | 1.0    |
| No log        | 0.09  | 200   | inf             | 0.9983 |
| No log        | 0.13  | 300   | inf             | 0.7672 |
| No log        | 0.18  | 400   | inf             | 0.6919 |
| 2.9929        | 0.22  | 500   | inf             | 0.6266 |
| 2.9929        | 0.26  | 600   | inf             | 0.5513 |
| 2.9929        | 0.31  | 700   | inf             | 0.5081 |
| 2.9929        | 0.35  | 800   | inf             | 0.4945 |
| 2.9929        | 0.39  | 900   | inf             | 0.4720 |
| 0.5311        | 0.44  | 1000  | inf             | 0.4387 |
| 0.5311        | 0.48  | 1100  | inf             | 0.4411 |
| 0.5311        | 0.53  | 1200  | inf             | 0.4429 |
| 0.5311        | 0.57  | 1300  | inf             | 0.4322 |
| 0.5311        | 0.61  | 1400  | inf             | 0.4532 |
| 0.4654        | 0.66  | 1500  | inf             | 0.4492 |
| 0.4654        | 0.7   | 1600  | inf             | 0.3879 |
| 0.4654        | 0.75  | 1700  | inf             | 0.3836 |
| 0.4654        | 0.79  | 1800  | inf             | 0.3743 |
| 0.4654        | 0.83  | 1900  | inf             | 0.3687 |
| 0.4254        | 0.88  | 2000  | inf             | 0.3793 |
| 0.4254        | 0.92  | 2100  | inf             | 0.3766 |
| 0.4254        | 0.97  | 2200  | inf             | 0.3705 |
| 0.4254        | 1.01  | 2300  | inf             | 0.3272 |
| 0.4254        | 1.05  | 2400  | inf             | 0.3185 |
| 0.3997        | 1.1   | 2500  | inf             | 0.3244 |
| 0.3997        | 1.14  | 2600  | inf             | 0.3082 |
| 0.3997        | 1.18  | 2700  | inf             | 0.3040 |
| 0.3997        | 1.23  | 2800  | inf             | 0.3028 |
| 0.3997        | 1.27  | 2900  | inf             | 0.3112 |
| 0.3668        | 1.32  | 3000  | inf             | 0.3110 |
| 0.3668        | 1.36  | 3100  | inf             | 0.3067 |
| 0.3668        | 1.4   | 3200  | inf             | 0.2961 |
| 0.3668        | 1.45  | 3300  | inf             | 0.3081 |
| 0.3668        | 1.49  | 3400  | inf             | 0.2936 |
| 0.3645        | 1.54  | 3500  | inf             | 0.3037 |
| 0.3645        | 1.58  | 3600  | inf             | 0.2974 |
| 0.3645        | 1.62  | 3700  | inf             | 0.3010 |
| 0.3645        | 1.67  | 3800  | inf             | 0.2985 |
| 0.3645        | 1.71  | 3900  | inf             | 0.2976 |
| 0.3624        | 1.76  | 4000  | inf             | 0.2928 |
| 0.3624        | 1.8   | 4100  | inf             | 0.2860 |
| 0.3624        | 1.84  | 4200  | inf             | 0.2922 |
| 0.3624        | 1.89  | 4300  | inf             | 0.2866 |
| 0.3624        | 1.93  | 4400  | inf             | 0.2776 |
| 0.3527        | 1.97  | 4500  | inf             | 0.2792 |
| 0.3527        | 2.02  | 4600  | inf             | 0.2858 |
| 0.3527        | 2.06  | 4700  | inf             | 0.2767 |
| 0.3527        | 2.11  | 4800  | inf             | 0.2824 |
| 0.3527        | 2.15  | 4900  | inf             | 0.2799 |
| 0.3162        | 2.19  | 5000  | inf             | 0.2673 |
| 0.3162        | 2.24  | 5100  | inf             | 0.2962 |
| 0.3162        | 2.28  | 5200  | inf             | 0.2736 |
| 0.3162        | 2.33  | 5300  | inf             | 0.2652 |
| 0.3162        | 2.37  | 5400  | inf             | 0.2551 |
| 0.3063        | 2.41  | 5500  | inf             | 0.2680 |
| 0.3063        | 2.46  | 5600  | inf             | 0.2558 |
| 0.3063        | 2.5   | 5700  | inf             | 0.2598 |
| 0.3063        | 2.54  | 5800  | inf             | 0.2518 |
| 0.3063        | 2.59  | 5900  | inf             | 0.2541 |
| 0.2913        | 2.63  | 6000  | inf             | 0.2507 |
| 0.2913        | 2.68  | 6100  | inf             | 0.2500 |
| 0.2913        | 2.72  | 6200  | inf             | 0.2435 |
| 0.2913        | 2.76  | 6300  | inf             | 0.2376 |
| 0.2913        | 2.81  | 6400  | inf             | 0.2348 |
| 0.2797        | 2.85  | 6500  | inf             | 0.2512 |
| 0.2797        | 2.9   | 6600  | inf             | 0.2382 |
| 0.2797        | 2.94  | 6700  | inf             | 0.2523 |
| 0.2797        | 2.98  | 6800  | inf             | 0.2522 |
| 0.2797        | 3.03  | 6900  | inf             | 0.2409 |
| 0.2766        | 3.07  | 7000  | inf             | 0.2453 |
| 0.2766        | 3.12  | 7100  | inf             | 0.2326 |
| 0.2766        | 3.16  | 7200  | inf             | 0.2286 |
| 0.2766        | 3.2   | 7300  | inf             | 0.2342 |
| 0.2766        | 3.25  | 7400  | inf             | 0.2305 |
| 0.2468        | 3.29  | 7500  | inf             | 0.2238 |
| 0.2468        | 3.33  | 7600  | inf             | 0.2321 |
| 0.2468        | 3.38  | 7700  | inf             | 0.2305 |
| 0.2468        | 3.42  | 7800  | inf             | 0.2174 |
| 0.2468        | 3.47  | 7900  | inf             | 0.2201 |
| 0.2439        | 3.51  | 8000  | inf             | 0.2133 |
| 0.2439        | 3.55  | 8100  | inf             | 0.2217 |
| 0.2439        | 3.6   | 8200  | inf             | 0.2189 |
| 0.2439        | 3.64  | 8300  | inf             | 0.2105 |
| 0.2439        | 3.69  | 8400  | inf             | 0.2118 |
| 0.2357        | 3.73  | 8500  | inf             | 0.2093 |
| 0.2357        | 3.77  | 8600  | inf             | 0.2103 |
| 0.2357        | 3.82  | 8700  | inf             | 0.2035 |
| 0.2357        | 3.86  | 8800  | inf             | 0.2019 |
| 0.2357        | 3.91  | 8900  | inf             | 0.2032 |
| 0.2217        | 3.95  | 9000  | inf             | 0.2056 |
| 0.2217        | 3.99  | 9100  | inf             | 0.2022 |
| 0.2217        | 4.04  | 9200  | inf             | 0.1932 |
| 0.2217        | 4.08  | 9300  | inf             | 0.1935 |
| 0.2217        | 4.12  | 9400  | inf             | 0.1906 |
| 0.2025        | 4.17  | 9500  | inf             | 0.1879 |
| 0.2025        | 4.21  | 9600  | inf             | 0.1882 |
| 0.2025        | 4.26  | 9700  | inf             | 0.1854 |
| 0.2025        | 4.3   | 9800  | inf             | 0.1865 |
| 0.2025        | 4.34  | 9900  | inf             | 0.1844 |
| 0.1869        | 4.39  | 10000 | inf             | 0.1822 |
| 0.1869        | 4.43  | 10100 | inf             | 0.1815 |
| 0.1869        | 4.48  | 10200 | inf             | 0.1812 |
| 0.1869        | 4.52  | 10300 | inf             | 0.1792 |
| 0.1869        | 4.56  | 10400 | inf             | 0.1797 |
| 0.1863        | 4.61  | 10500 | inf             | 0.1774 |
| 0.1863        | 4.65  | 10600 | inf             | 0.1767 |
| 0.1863        | 4.7   | 10700 | inf             | 0.1765 |
| 0.1863        | 4.74  | 10800 | inf             | 0.1753 |
| 0.1863        | 4.78  | 10900 | inf             | 0.1731 |
| 0.178         | 4.83  | 11000 | inf             | 0.1727 |
| 0.178         | 4.87  | 11100 | inf             | 0.1724 |
| 0.178         | 4.91  | 11200 | inf             | 0.1722 |
| 0.178         | 4.96  | 11300 | inf             | 0.1712 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
