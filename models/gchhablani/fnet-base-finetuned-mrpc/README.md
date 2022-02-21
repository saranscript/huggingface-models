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
- accuracy
- f1
model-index:
- name: fnet-base-finetuned-mrpc
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE MRPC
      type: glue
      args: mrpc
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.7720588235294118
    - name: F1
      type: f1
      value: 0.8502415458937198
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# fnet-base-finetuned-mrpc

This model is a fine-tuned version of [google/fnet-base](https://huggingface.co/google/fnet-base) on the GLUE MRPC dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9653
- Accuracy: 0.7721
- F1: 0.8502
- Combined Score: 0.8112

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

python ../run_glue.py \\n  --model_name_or_path google/fnet-base \\n  --task_name mrpc \\n  --do_train \\n  --do_eval \\n  --max_seq_length 512 \\n  --per_device_train_batch_size 16 \\n  --learning_rate 2e-5 \\n  --num_train_epochs 5 \\n  --output_dir fnet-base-finetuned-mrpc \\n  --push_to_hub \\n  --hub_strategy all_checkpoints \\n  --logging_strategy epoch \\n  --save_strategy epoch \\n  --evaluation_strategy epoch \\n```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Combined Score |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:--------------:|
| 0.544         | 1.0   | 230  | 0.5272          | 0.7328   | 0.8300 | 0.7814         |
| 0.4034        | 2.0   | 460  | 0.6211          | 0.7255   | 0.8298 | 0.7776         |
| 0.2602        | 3.0   | 690  | 0.9110          | 0.7230   | 0.8306 | 0.7768         |
| 0.1688        | 4.0   | 920  | 0.8640          | 0.7696   | 0.8489 | 0.8092         |
| 0.0913        | 5.0   | 1150 | 0.9653          | 0.7721   | 0.8502 | 0.8112         |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
