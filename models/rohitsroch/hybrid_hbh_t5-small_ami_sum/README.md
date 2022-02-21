---
tags:
- generated_from_trainer
model_index:
- name: hybrid_hbh_t5-small_ami_sum
  results:
  - task:
      name: Summarization
      type: summarization
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hybrid_hbh_t5-small_ami_sum

This model is a fine-tuned version of [t5-small](https://huggingface.co/best-models/H) on an AMI dataset for dialogue summarization task.

## Model description

More information needed

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 100.0
- label_smoothing_factor: 0.1

### Results on Test Set

- predict_gen_len            =      329.2
- predict_rouge1             =    **48.7673**
- predict_rouge2             =    **18.1832**
- predict_rougeL             =    **26.1713**
- predict_rougeLsum          =    **46.8434**
- predict_samples            =         20
- predict_samples_per_second =      1.098
- predict_steps_per_second   =      0.274


### Framework versions

- Transformers 4.8.0
- Pytorch 1.6.0
- Datasets 1.10.2
- Tokenizers 0.10.3
