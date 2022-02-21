---
language:
- en
license: apache-2.0
tags:
- generated_from_trainer
- fnet-bert-base-comparison
datasets:
- glue
metrics:
- spearmanr
model-index:
- name: bert-base-cased-finetuned-stsb
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE STSB
      type: glue
      args: stsb
    metrics:
    - name: Spearmanr
      type: spearmanr
      value: 0.8897907271421561
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-cased-finetuned-stsb

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the GLUE STSB dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4861
- Pearson: 0.8926
- Spearmanr: 0.8898
- Combined Score: 0.8912

The model was fine-tuned to compare [google/fnet-base](https://huggingface.co/google/fnet-base) as introduced in [this paper](https://arxiv.org/abs/2105.03824) against [bert-base-cased](https://huggingface.co/bert-base-cased).

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

This model is trained using the [run_glue](https://github.com/huggingface/transformers/blob/master/examples/pytorch/text-classification/run_glue.py) script. The following command was used:

```bash
#!/usr/bin/bash

python ../run_glue.py \\n  --model_name_or_path bert-base-cased \\n  --task_name stsb \\n  --do_train \\n  --do_eval \\n  --max_seq_length 512 \\n  --per_device_train_batch_size 16 \\n  --learning_rate 2e-5 \\n  --num_train_epochs 3 \\n  --output_dir bert-base-cased-finetuned-stsb \\n  --push_to_hub \\n  --hub_strategy all_checkpoints \\n  --logging_strategy epoch \\n  --save_strategy epoch \\n  --evaluation_strategy epoch \\n```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Combined Score | Validation Loss | Pearson | Spearmanr |
|:-------------:|:-----:|:----:|:--------------:|:---------------:|:-------:|:---------:|
| 1.1174        | 1.0   | 360  | 0.8816         | 0.5000          | 0.8832  | 0.8800    |
| 0.3835        | 2.0   | 720  | 0.8901         | 0.4672          | 0.8915  | 0.8888    |
| 0.2388        | 3.0   | 1080 | 0.8912         | 0.4861          | 0.8926  | 0.8898    |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
