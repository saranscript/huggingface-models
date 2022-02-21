---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xlsr-53-demo-colab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-53-demo-colab

This model is a fine-tuned version of [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 6.7860
- Wer: 1.1067

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
- num_epochs: 1000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 8.2273        | 44.42  | 400  | 3.3544          | 1.0    |
| 0.9228        | 88.84  | 800  | 4.7054          | 1.1601 |
| 0.1423        | 133.32 | 1200 | 5.9489          | 1.1578 |
| 0.0751        | 177.74 | 1600 | 5.5939          | 1.1717 |
| 0.0554        | 222.21 | 2000 | 6.1230          | 1.1717 |
| 0.0356        | 266.63 | 2400 | 6.2845          | 1.1613 |
| 0.0288        | 311.11 | 2800 | 6.6109          | 1.2100 |
| 0.0223        | 355.53 | 3200 | 6.5605          | 1.1299 |
| 0.0197        | 399.95 | 3600 | 7.1242          | 1.1682 |
| 0.0171        | 444.42 | 4000 | 7.2452          | 1.1578 |
| 0.0149        | 488.84 | 4400 | 7.4048          | 1.0684 |
| 0.0118        | 533.32 | 4800 | 6.6227          | 1.1172 |
| 0.011         | 577.74 | 5200 | 6.7909          | 1.1566 |
| 0.0095        | 622.21 | 5600 | 6.8088          | 1.1102 |
| 0.0077        | 666.63 | 6000 | 7.4451          | 1.1311 |
| 0.0062        | 711.11 | 6400 | 6.8486          | 1.0777 |
| 0.0051        | 755.53 | 6800 | 6.8812          | 1.1241 |
| 0.0051        | 799.95 | 7200 | 6.9987          | 1.1450 |
| 0.0041        | 844.42 | 7600 | 7.3048          | 1.1323 |
| 0.0044        | 888.84 | 8000 | 6.6644          | 1.1125 |
| 0.0031        | 933.32 | 8400 | 6.6298          | 1.1148 |
| 0.0027        | 977.74 | 8800 | 6.7860          | 1.1067 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
