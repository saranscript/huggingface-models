---
license: apache-2.0
tags:
- automatic-speech-recognition
model-index:
- name: wav2vec2-large-xlsr-czech-1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-czech-1

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5847
- Wer: 0.3666

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
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 5.44          | 0.56  | 500   | 1.3705          | 0.9861 |
| 0.8205        | 1.12  | 1000  | 0.7485          | 0.7268 |
| 0.4858        | 1.68  | 1500  | 0.6293          | 0.6444 |
| 0.4071        | 2.24  | 2000  | 0.5579          | 0.5781 |
| 0.3316        | 2.8   | 2500  | 0.5407          | 0.5731 |
| 0.2971        | 3.36  | 3000  | 0.5330          | 0.5501 |
| 0.2775        | 3.92  | 3500  | 0.4898          | 0.5410 |
| 0.2386        | 4.48  | 4000  | 0.4933          | 0.5288 |
| 0.2469        | 5.04  | 4500  | 0.5545          | 0.5277 |
| 0.2181        | 5.61  | 5000  | 0.5076          | 0.5140 |
| 0.195         | 6.17  | 5500  | 0.5647          | 0.5192 |
| 0.1975        | 6.73  | 6000  | 0.5752          | 0.5051 |
| 0.1813        | 7.29  | 6500  | 0.5200          | 0.4976 |
| 0.1783        | 7.85  | 7000  | 0.5672          | 0.5071 |
| 0.1601        | 8.41  | 7500  | 0.5726          | 0.4847 |
| 0.1565        | 8.97  | 8000  | 0.5653          | 0.4750 |
| 0.1448        | 9.53  | 8500  | 0.5201          | 0.4726 |
| 0.1418        | 10.09 | 9000  | 0.5592          | 0.4800 |
| 0.1412        | 10.65 | 9500  | 0.5332          | 0.4691 |
| 0.1309        | 11.21 | 10000 | 0.5484          | 0.4565 |
| 0.1293        | 11.77 | 10500 | 0.5880          | 0.4828 |
| 0.1204        | 12.33 | 11000 | 0.6207          | 0.4723 |
| 0.1177        | 12.89 | 11500 | 0.5383          | 0.4468 |
| 0.1062        | 13.45 | 12000 | 0.6132          | 0.4618 |
| 0.1023        | 14.01 | 12500 | 0.5882          | 0.4489 |
| 0.0971        | 14.57 | 13000 | 0.5645          | 0.4330 |
| 0.0926        | 15.13 | 13500 | 0.5913          | 0.4324 |
| 0.0895        | 15.69 | 14000 | 0.5487          | 0.4291 |
| 0.0838        | 16.26 | 14500 | 0.5490          | 0.4197 |
| 0.0816        | 16.82 | 15000 | 0.5726          | 0.4419 |
| 0.0832        | 17.38 | 15500 | 0.5825          | 0.4204 |
| 0.0759        | 17.94 | 16000 | 0.5688          | 0.4340 |
| 0.0727        | 18.5  | 16500 | 0.5753          | 0.4274 |
| 0.0706        | 19.06 | 17000 | 0.5883          | 0.4108 |
| 0.065         | 19.62 | 17500 | 0.5898          | 0.4003 |
| 0.0617        | 20.18 | 18000 | 0.6078          | 0.3995 |
| 0.0624        | 20.74 | 18500 | 0.5864          | 0.3954 |
| 0.0575        | 21.3  | 19000 | 0.5767          | 0.3921 |
| 0.0643        | 21.86 | 19500 | 0.5952          | 0.3909 |
| 0.0606        | 22.42 | 20000 | 0.5917          | 0.3892 |
| 0.055         | 22.98 | 20500 | 0.5669          | 0.3784 |
| 0.0521        | 23.54 | 21000 | 0.6058          | 0.3875 |
| 0.0514        | 24.1  | 21500 | 0.6009          | 0.3804 |
| 0.0502        | 24.66 | 22000 | 0.5812          | 0.3754 |
| 0.0515        | 25.22 | 22500 | 0.5815          | 0.3721 |
| 0.0473        | 25.78 | 23000 | 0.5917          | 0.3721 |
| 0.049         | 26.35 | 23500 | 0.5709          | 0.3692 |
| 0.0487        | 26.91 | 24000 | 0.5784          | 0.3690 |
| 0.0472        | 27.47 | 24500 | 0.5754          | 0.3675 |
| 0.0472        | 28.03 | 25000 | 0.5829          | 0.3675 |
| 0.0456        | 28.59 | 25500 | 0.5842          | 0.3675 |
| 0.0453        | 29.15 | 26000 | 0.5852          | 0.3669 |
| 0.0498        | 29.71 | 26500 | 0.5847          | 0.3666 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
