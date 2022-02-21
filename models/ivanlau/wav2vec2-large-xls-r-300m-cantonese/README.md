---
language:
- zh-HK
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- zh-HK
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Chinese_HongKong (Cantonese)
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: zh-HK
    metrics:
       - name: Test WER
         type: wer
         value: 0.8111349803079126
       - name: Test CER
         type: cer
         value: 0.21962250882996914
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: zh-HK
    metrics:
       - name: Test WER
         type: wer
         value: 1.0
       - name: Test CER
         type: cer
         value: 0.6160564326503191
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: zh-HK
    metrics:
       - name: Test WER with LM
         type: wer
         value: 0.8055853920515574
       - name: Test CER with LM
         type: cer
         value: 0.21578686612008757
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: zh-HK
    metrics:
       - name: Test WER with LM
         type: wer
         value: 1.0012453300124533
       - name: Test CER with LM
         type: cer
         value: 0.6153006382264025
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - ZH-HK dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4848
- Wer: 0.8004

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
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| No log        | 1.0   | 183   | 47.8442         | 1.0    |
| No log        | 2.0   | 366   | 6.3109          | 1.0    |
| 41.8902       | 3.0   | 549   | 6.2392          | 1.0    |
| 41.8902       | 4.0   | 732   | 5.9739          | 1.1123 |
| 41.8902       | 5.0   | 915   | 4.9014          | 1.9474 |
| 5.5817        | 6.0   | 1098  | 3.9892          | 1.0188 |
| 5.5817        | 7.0   | 1281  | 3.5080          | 1.0104 |
| 5.5817        | 8.0   | 1464  | 3.0797          | 0.9905 |
| 3.5579        | 9.0   | 1647  | 2.8111          | 0.9836 |
| 3.5579        | 10.0  | 1830  | 2.6726          | 0.9815 |
| 2.7771        | 11.0  | 2013  | 2.7177          | 0.9809 |
| 2.7771        | 12.0  | 2196  | 2.3582          | 0.9692 |
| 2.7771        | 13.0  | 2379  | 2.1708          | 0.9757 |
| 2.3488        | 14.0  | 2562  | 2.0491          | 0.9526 |
| 2.3488        | 15.0  | 2745  | 1.8518          | 0.9378 |
| 2.3488        | 16.0  | 2928  | 1.6845          | 0.9286 |
| 1.7859        | 17.0  | 3111  | 1.6412          | 0.9280 |
| 1.7859        | 18.0  | 3294  | 1.5488          | 0.9035 |
| 1.7859        | 19.0  | 3477  | 1.4546          | 0.9010 |
| 1.3898        | 20.0  | 3660  | 1.5147          | 0.9201 |
| 1.3898        | 21.0  | 3843  | 1.4467          | 0.8959 |
| 1.1291        | 22.0  | 4026  | 1.4743          | 0.9035 |
| 1.1291        | 23.0  | 4209  | 1.3827          | 0.8762 |
| 1.1291        | 24.0  | 4392  | 1.3437          | 0.8792 |
| 0.8993        | 25.0  | 4575  | 1.2895          | 0.8577 |
| 0.8993        | 26.0  | 4758  | 1.2928          | 0.8558 |
| 0.8993        | 27.0  | 4941  | 1.2947          | 0.9163 |
| 0.6298        | 28.0  | 5124  | 1.3151          | 0.8738 |
| 0.6298        | 29.0  | 5307  | 1.2972          | 0.8514 |
| 0.6298        | 30.0  | 5490  | 1.3030          | 0.8432 |
| 0.4757        | 31.0  | 5673  | 1.3264          | 0.8364 |
| 0.4757        | 32.0  | 5856  | 1.3131          | 0.8421 |
| 0.3735        | 33.0  | 6039  | 1.3457          | 0.8588 |
| 0.3735        | 34.0  | 6222  | 1.3450          | 0.8473 |
| 0.3735        | 35.0  | 6405  | 1.3452          | 0.9218 |
| 0.3253        | 36.0  | 6588  | 1.3754          | 0.8397 |
| 0.3253        | 37.0  | 6771  | 1.3554          | 0.8353 |
| 0.3253        | 38.0  | 6954  | 1.3532          | 0.8312 |
| 0.2816        | 39.0  | 7137  | 1.3694          | 0.8345 |
| 0.2816        | 40.0  | 7320  | 1.3953          | 0.8296 |
| 0.2397        | 41.0  | 7503  | 1.3858          | 0.8293 |
| 0.2397        | 42.0  | 7686  | 1.3959          | 0.8402 |
| 0.2397        | 43.0  | 7869  | 1.4350          | 0.9318 |
| 0.2084        | 44.0  | 8052  | 1.4004          | 0.8806 |
| 0.2084        | 45.0  | 8235  | 1.3871          | 0.8255 |
| 0.2084        | 46.0  | 8418  | 1.4060          | 0.8252 |
| 0.1853        | 47.0  | 8601  | 1.3992          | 0.8501 |
| 0.1853        | 48.0  | 8784  | 1.4186          | 0.8252 |
| 0.1853        | 49.0  | 8967  | 1.4120          | 0.8165 |
| 0.1671        | 50.0  | 9150  | 1.4166          | 0.8214 |
| 0.1671        | 51.0  | 9333  | 1.4411          | 0.8501 |
| 0.1513        | 52.0  | 9516  | 1.4692          | 0.8394 |
| 0.1513        | 53.0  | 9699  | 1.4640          | 0.8391 |
| 0.1513        | 54.0  | 9882  | 1.4501          | 0.8419 |
| 0.133         | 55.0  | 10065 | 1.4134          | 0.8351 |
| 0.133         | 56.0  | 10248 | 1.4593          | 0.8405 |
| 0.133         | 57.0  | 10431 | 1.4560          | 0.8389 |
| 0.1198        | 58.0  | 10614 | 1.4734          | 0.8334 |
| 0.1198        | 59.0  | 10797 | 1.4649          | 0.8318 |
| 0.1198        | 60.0  | 10980 | 1.4659          | 0.8100 |
| 0.1109        | 61.0  | 11163 | 1.4784          | 0.8119 |
| 0.1109        | 62.0  | 11346 | 1.4938          | 0.8149 |
| 0.1063        | 63.0  | 11529 | 1.5050          | 0.8152 |
| 0.1063        | 64.0  | 11712 | 1.4773          | 0.8176 |
| 0.1063        | 65.0  | 11895 | 1.4836          | 0.8261 |
| 0.0966        | 66.0  | 12078 | 1.4979          | 0.8157 |
| 0.0966        | 67.0  | 12261 | 1.4603          | 0.8048 |
| 0.0966        | 68.0  | 12444 | 1.4803          | 0.8127 |
| 0.0867        | 69.0  | 12627 | 1.4974          | 0.8130 |
| 0.0867        | 70.0  | 12810 | 1.4721          | 0.8078 |
| 0.0867        | 71.0  | 12993 | 1.4644          | 0.8192 |
| 0.0827        | 72.0  | 13176 | 1.4835          | 0.8138 |
| 0.0827        | 73.0  | 13359 | 1.4934          | 0.8122 |
| 0.0734        | 74.0  | 13542 | 1.4951          | 0.8062 |
| 0.0734        | 75.0  | 13725 | 1.4908          | 0.8070 |
| 0.0734        | 76.0  | 13908 | 1.4876          | 0.8124 |
| 0.0664        | 77.0  | 14091 | 1.4934          | 0.8053 |
| 0.0664        | 78.0  | 14274 | 1.4603          | 0.8048 |
| 0.0664        | 79.0  | 14457 | 1.4732          | 0.8073 |
| 0.0602        | 80.0  | 14640 | 1.4925          | 0.8078 |
| 0.0602        | 81.0  | 14823 | 1.4812          | 0.8064 |
| 0.057         | 82.0  | 15006 | 1.4950          | 0.8013 |
| 0.057         | 83.0  | 15189 | 1.4785          | 0.8056 |
| 0.057         | 84.0  | 15372 | 1.4856          | 0.7993 |
| 0.0517        | 85.0  | 15555 | 1.4755          | 0.8034 |
| 0.0517        | 86.0  | 15738 | 1.4813          | 0.8034 |
| 0.0517        | 87.0  | 15921 | 1.4966          | 0.8048 |
| 0.0468        | 88.0  | 16104 | 1.4883          | 0.8002 |
| 0.0468        | 89.0  | 16287 | 1.4746          | 0.8023 |
| 0.0468        | 90.0  | 16470 | 1.4697          | 0.7974 |
| 0.0426        | 91.0  | 16653 | 1.4775          | 0.8004 |
| 0.0426        | 92.0  | 16836 | 1.4852          | 0.8023 |
| 0.0387        | 93.0  | 17019 | 1.4868          | 0.8004 |
| 0.0387        | 94.0  | 17202 | 1.4785          | 0.8021 |
| 0.0387        | 95.0  | 17385 | 1.4892          | 0.8015 |
| 0.0359        | 96.0  | 17568 | 1.4862          | 0.8018 |
| 0.0359        | 97.0  | 17751 | 1.4851          | 0.8007 |
| 0.0359        | 98.0  | 17934 | 1.4846          | 0.7999 |
| 0.0347        | 99.0  | 18117 | 1.4852          | 0.7993 |
| 0.0347        | 100.0 | 18300 | 1.4848          | 0.8004 |


#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id ivanlau/wav2vec2-large-xls-r-300m-cantonese --dataset mozilla-foundation/common_voice_8_0 --config zh-HK --split test --log_outputs
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id ivanlau/wav2vec2-large-xls-r-300m-cantonese --dataset speech-recognition-community-v2/dev_data --config zh-HK --split validation --chunk_length_s 5.0 --stride_length_s 1.0 --log_outputs
```

### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
