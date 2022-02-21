---
tags:
- generated_from_trainer
model-index:
- name: feedback-lf-base
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# feedback-lf-base

This model is a fine-tuned version of [allenai/longformer-base-4096](https://huggingface.co/allenai/longformer-base-4096) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7450
- Claim Precision: 0.2089
- Claim Recall: 0.3358
- Claim F1: 0.2575
- Claim Number: 6850
- Concluding statement Precision: 0.3112
- Concluding statement Recall: 0.5090
- Concluding statement F1: 0.3862
- Concluding statement Number: 2281
- Counterclaim Precision: 0.2158
- Counterclaim Recall: 0.3602
- Counterclaim F1: 0.2699
- Counterclaim Number: 1016
- Evidence Precision: 0.1723
- Evidence Recall: 0.3141
- Evidence F1: 0.2225
- Evidence Number: 6953
- Lead Precision: 0.4032
- Lead Recall: 0.5723
- Lead F1: 0.4731
- Lead Number: 1660
- Position Precision: 0.3597
- Position Recall: 0.4762
- Position F1: 0.4098
- Position Number: 2589
- Rebuttal Precision: 0.1387
- Rebuttal Recall: 0.2742
- Rebuttal F1: 0.1842
- Rebuttal Number: 755
- Overall Precision: 0.2308
- Overall Recall: 0.3801
- Overall F1: 0.2872
- Overall Accuracy: 0.7790
- Cv f1: 0.5896

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
| 0.8045        | 0.72  | 150  | 0.7620          | 0.0702          | 0.0984       | 0.0819   | 6850         | 0.1279                         | 0.2249                      | 0.1630                  | 2281                        | 0.0147                 | 0.0108              | 0.0125          | 1016                | 0.0650             | 0.1129          | 0.0825      | 6953            | 0.1318         | 0.3277      | 0.1879  | 1660        | 0.175              | 0.2731          | 0.2133      | 2589            | 0.0209             | 0.0053          | 0.0085      | 755             | 0.0931            | 0.1465         | 0.1138     | 0.7578           | 0.3259 |
| 0.648         | 1.45  | 300  | 0.6794          | 0.1117          | 0.2085       | 0.1454   | 6850         | 0.1839                         | 0.3705                      | 0.2458                  | 2281                        | 0.1120                 | 0.2175              | 0.1479          | 1016                | 0.1009             | 0.2271          | 0.1398      | 6953            | 0.2362         | 0.4681      | 0.3139  | 1660        | 0.2815             | 0.4029          | 0.3314      | 2589            | 0.0726             | 0.1815          | 0.1037      | 755             | 0.1374            | 0.2728         | 0.1828     | 0.7713           | 0.5308 |
| 0.5667        | 2.17  | 450  | 0.6606          | 0.1721          | 0.3153       | 0.2226   | 6850         | 0.2514                         | 0.4020                      | 0.3094                  | 2281                        | 0.1692                 | 0.3120              | 0.2195          | 1016                | 0.1539             | 0.2861          | 0.2001      | 6953            | 0.3328         | 0.5271      | 0.4080  | 1660        | 0.3427             | 0.4662          | 0.3950      | 2589            | 0.1307             | 0.2411          | 0.1695      | 755             | 0.1984            | 0.3460         | 0.2522     | 0.7795           | 0.558  |
| 0.5438        | 2.9   | 600  | 0.6380          | 0.2056          | 0.3093       | 0.2470   | 6850         | 0.2536                         | 0.4055                      | 0.3120                  | 2281                        | 0.1848                 | 0.3425              | 0.2401          | 1016                | 0.1644             | 0.2918          | 0.2103      | 6953            | 0.3570         | 0.5669      | 0.4381  | 1660        | 0.3534             | 0.4670          | 0.4023      | 2589            | 0.1341             | 0.2411          | 0.1723      | 755             | 0.2178            | 0.3508         | 0.2687     | 0.7848           | 0.5667 |
| 0.4573        | 3.62  | 750  | 0.6690          | 0.1889          | 0.2964       | 0.2308   | 6850         | 0.2957                         | 0.5129                      | 0.3751                  | 2281                        | 0.1807                 | 0.3356              | 0.2349          | 1016                | 0.1608             | 0.3010          | 0.2096      | 6953            | 0.3488         | 0.5464      | 0.4258  | 1660        | 0.3461             | 0.4650          | 0.3968      | 2589            | 0.1217             | 0.2755          | 0.1688      | 755             | 0.2127            | 0.3598         | 0.2673     | 0.7825           | 0.5824 |
| 0.3923        | 4.35  | 900  | 0.7032          | 0.1925          | 0.3330       | 0.2440   | 6850         | 0.2932                         | 0.5033                      | 0.3706                  | 2281                        | 0.1969                 | 0.3219              | 0.2443          | 1016                | 0.1627             | 0.3141          | 0.2143      | 6953            | 0.3650         | 0.5422      | 0.4363  | 1660        | 0.3552             | 0.4705          | 0.4048      | 2589            | 0.1315             | 0.2623          | 0.1751      | 755             | 0.2158            | 0.3735         | 0.2736     | 0.7803           | 0.5902 |
| 0.3779        | 5.07  | 1050 | 0.7310          | 0.2202          | 0.3150       | 0.2592   | 6850         | 0.3230                         | 0.5059                      | 0.3943                  | 2281                        | 0.2077                 | 0.3681              | 0.2655          | 1016                | 0.1808             | 0.3112          | 0.2287      | 6953            | 0.4055         | 0.5813      | 0.4777  | 1660        | 0.3690             | 0.4743          | 0.4151      | 2589            | 0.1417             | 0.2715          | 0.1862      | 755             | 0.2405            | 0.3731         | 0.2925     | 0.7830           | 0.5866 |
| 0.3291        | 5.8   | 1200 | 0.7499          | 0.2067          | 0.3336       | 0.2552   | 6850         | 0.3086                         | 0.5059                      | 0.3834                  | 2281                        | 0.2074                 | 0.3543              | 0.2616          | 1016                | 0.1720             | 0.3140          | 0.2222      | 6953            | 0.3943         | 0.5801      | 0.4695  | 1660        | 0.3479             | 0.4813          | 0.4039      | 2589            | 0.1375             | 0.2715          | 0.1825      | 755             | 0.2285            | 0.3798         | 0.2854     | 0.7788           | 0.5903 |


### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.9.0a0+c3d40fd
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
