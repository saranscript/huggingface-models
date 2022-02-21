---
tags:
- generated_from_trainer
model_index:
- name: hybrid_hbh_bart-base_icsi_sum
  results:
  - task:
      name: Summarization
      type: summarization
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hybrid_hbh_bart-base_icsi_sum

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on ICSI dataset for dialogue summarization task.

## Model description

More information needed

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0005
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 100.0
- label_smoothing_factor: 0.1

### Results on Test Set

- predict_gen_len           =      480.0 
- predict_rouge1             =    **46.8707** 
- predict_rouge2             =    **10.1337** 
- predict_rougeL             =    **19.3386** 
- predict_rougeLsum          =    **43.6989** 
- predict_samples            =          6 
- predict_samples_per_second =       0.54 
- predict_steps_per_second   =       0.27 

### Framework versions

- Transformers 4.8.0
- Pytorch 1.6.0
- Datasets 1.10.2
- Tokenizers 0.10.3
