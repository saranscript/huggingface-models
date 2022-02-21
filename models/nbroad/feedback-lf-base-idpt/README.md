---
tags:
- generated_from_trainer
model-index:
- name: feedback-lf-base-idpt
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# feedback-lf-base-idpt

This model was trained from scratch on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7503
- Claim Precision: 0.2334
- Claim Recall: 0.3733
- Claim F1: 0.2872
- Claim Number: 6850
- Concluding statement Precision: 0.3434
- Concluding statement Recall: 0.5199
- Concluding statement F1: 0.4136
- Concluding statement Number: 2281
- Counterclaim Precision: 0.2457
- Counterclaim Recall: 0.3957
- Counterclaim F1: 0.3032
- Counterclaim Number: 1016
- Evidence Precision: 0.1911
- Evidence Recall: 0.3229
- Evidence F1: 0.2401
- Evidence Number: 6953
- Lead Precision: 0.4385
- Lead Recall: 0.6036
- Lead F1: 0.5080
- Lead Number: 1660
- Position Precision: 0.3808
- Position Recall: 0.5052
- Position F1: 0.4343
- Position Number: 2589
- Rebuttal Precision: 0.1601
- Rebuttal Recall: 0.3126
- Rebuttal F1: 0.2118
- Rebuttal Number: 755
- Overall Precision: 0.2554
- Overall Recall: 0.4043
- Overall F1: 0.3131
- Overall Accuracy: 0.7817
- Cv f1: 0.5932

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 8
- eval_batch_size: 32
- seed: 1881
- distributed_type: multi-GPU
- num_devices: 4
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- total_eval_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 6
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Claim Precision | Claim Recall | Claim F1 | Claim Number | Concluding statement Precision | Concluding statement Recall | Concluding statement F1 | Concluding statement Number | Counterclaim Precision | Counterclaim Recall | Counterclaim F1 | Counterclaim Number | Evidence Precision | Evidence Recall | Evidence F1 | Evidence Number | Lead Precision | Lead Recall | Lead F1 | Lead Number | Position Precision | Position Recall | Position F1 | Position Number | Rebuttal Precision | Rebuttal Recall | Rebuttal F1 | Rebuttal Number | Overall Precision | Overall Recall | Overall F1 | Overall Accuracy | Cv f1  |
|:-------------:|:-----:|:----:|:---------------:|:---------------:|:------------:|:--------:|:------------:|:------------------------------:|:---------------------------:|:-----------------------:|:---------------------------:|:----------------------:|:-------------------:|:---------------:|:-------------------:|:------------------:|:---------------:|:-----------:|:---------------:|:--------------:|:-----------:|:-------:|:-----------:|:------------------:|:---------------:|:-----------:|:---------------:|:------------------:|:---------------:|:-----------:|:---------------:|:-----------------:|:--------------:|:----------:|:----------------:|:------:|
| 0.7772        | 0.72  | 150  | 0.7469          | 0.0505          | 0.0888       | 0.0643   | 6850         | 0.1228                         | 0.2762                      | 0.1700                  | 2281                        | 0.0223                 | 0.0236              | 0.0229          | 1016                | 0.0549             | 0.1464          | 0.0799      | 6953            | 0.0817         | 0.1566      | 0.1074  | 1660        | 0.1593             | 0.2754          | 0.2019      | 2589            | 0.0136             | 0.0079          | 0.0100      | 755             | 0.0726            | 0.1474         | 0.0973     | 0.7578           | 0.4128 |
| 0.6339        | 1.45  | 300  | 0.6703          | 0.1326          | 0.2036       | 0.1606   | 6850         | 0.2133                         | 0.3762                      | 0.2722                  | 2281                        | 0.1662                 | 0.2451              | 0.1981          | 1016                | 0.1194             | 0.2304          | 0.1573      | 6953            | 0.2755         | 0.4693      | 0.3471  | 1660        | 0.3053             | 0.3905          | 0.3427      | 2589            | 0.0774             | 0.1536          | 0.1029      | 755             | 0.1620            | 0.2719         | 0.2030     | 0.7780           | 0.5237 |
| 0.5547        | 2.17  | 450  | 0.6471          | 0.1625          | 0.2728       | 0.2037   | 6850         | 0.2551                         | 0.4625                      | 0.3288                  | 2281                        | 0.1877                 | 0.3100              | 0.2339          | 1016                | 0.1413             | 0.2569          | 0.1823      | 6953            | 0.3073         | 0.5386      | 0.3913  | 1660        | 0.3007             | 0.4272          | 0.3530      | 2589            | 0.1157             | 0.1974          | 0.1459      | 755             | 0.1896            | 0.3246         | 0.2394     | 0.7865           | 0.5635 |
| 0.5376        | 2.9   | 600  | 0.6443          | 0.2327          | 0.3210       | 0.2698   | 6850         | 0.3165                         | 0.4682                      | 0.3777                  | 2281                        | 0.1995                 | 0.3484              | 0.2538          | 1016                | 0.1948             | 0.2945          | 0.2345      | 6953            | 0.4087         | 0.5825      | 0.4804  | 1660        | 0.3845             | 0.4871          | 0.4297      | 2589            | 0.1548             | 0.2437          | 0.1893      | 755             | 0.2530            | 0.3656         | 0.2990     | 0.7906           | 0.5672 |
| 0.4465        | 3.62  | 750  | 0.6712          | 0.2214          | 0.3552       | 0.2728   | 6850         | 0.3228                         | 0.5235                      | 0.3993                  | 2281                        | 0.2333                 | 0.3888              | 0.2916          | 1016                | 0.1909             | 0.3183          | 0.2387      | 6953            | 0.3989         | 0.5861      | 0.4747  | 1660        | 0.3611             | 0.5064          | 0.4215      | 2589            | 0.1516             | 0.2848          | 0.1979      | 755             | 0.2463            | 0.3951         | 0.3035     | 0.7865           | 0.5936 |
| 0.3766        | 4.35  | 900  | 0.7101          | 0.2239          | 0.3616       | 0.2765   | 6850         | 0.3453                         | 0.5392                      | 0.4210                  | 2281                        | 0.2437                 | 0.3809              | 0.2972          | 1016                | 0.1940             | 0.3180          | 0.2410      | 6953            | 0.4459         | 0.5982      | 0.5109  | 1660        | 0.3719             | 0.5017          | 0.4272      | 2589            | 0.1521             | 0.2927          | 0.2002      | 755             | 0.2535            | 0.3989         | 0.3100     | 0.7848           | 0.5933 |
| 0.3603        | 5.07  | 1050 | 0.7490          | 0.2386          | 0.3508       | 0.2840   | 6850         | 0.3456                         | 0.5239                      | 0.4164                  | 2281                        | 0.2352                 | 0.4055              | 0.2977          | 1016                | 0.1960             | 0.3214          | 0.2435      | 6953            | 0.4262         | 0.6090      | 0.5015  | 1660        | 0.3876             | 0.5052          | 0.4386      | 2589            | 0.1759             | 0.2901          | 0.219       | 755             | 0.2608            | 0.3973         | 0.3149     | 0.7847           | 0.5913 |
| 0.3124        | 5.8   | 1200 | 0.7523          | 0.2321          | 0.3723       | 0.2859   | 6850         | 0.3531                         | 0.5322                      | 0.4245                  | 2281                        | 0.2444                 | 0.4006              | 0.3036          | 1016                | 0.1888             | 0.3197          | 0.2374      | 6953            | 0.4350         | 0.6048      | 0.5060  | 1660        | 0.3774             | 0.5071          | 0.4328      | 2589            | 0.1538             | 0.3113          | 0.2059      | 755             | 0.2543            | 0.4047         | 0.3123     | 0.7807           | 0.5939 |


### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.9.0a0+c3d40fd
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
