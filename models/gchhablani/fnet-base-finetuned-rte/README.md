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
model-index:
- name: fnet-base-finetuned-rte
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE RTE
      type: glue
      args: rte
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.628158844765343
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# fnet-base-finetuned-rte

This model is a fine-tuned version of [google/fnet-base](https://huggingface.co/google/fnet-base) on the GLUE RTE dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6978
- Accuracy: 0.6282

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


python ../run_glue.py \\n  --model_name_or_path google/fnet-base \\n  --task_name rte \\n  --do_train \\n  --do_eval \\n  --max_seq_length 512 \\n  --per_device_train_batch_size 16 \\n  --learning_rate 2e-5 \\n  --num_train_epochs 3 \\n  --output_dir fnet-base-finetuned-rte \\n  --push_to_hub \\n  --hub_strategy all_checkpoints \\n  --logging_strategy epoch \\n  --save_strategy epoch \\n  --evaluation_strategy epoch \\n```

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

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.6829        | 1.0   | 156  | 0.6657          | 0.5704   |
| 0.6174        | 2.0   | 312  | 0.6784          | 0.6101   |
| 0.5141        | 3.0   | 468  | 0.6978          | 0.6282   |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
