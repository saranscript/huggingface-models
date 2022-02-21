---
model-index:
- name: feedback-prize-bigbird-base
  results: []
---

# feedback-prize-bigbird-base

This model is a fine-tuned version of [google/bigbird-roberta-base](https://huggingface.co/google/bigbird-roberta-base) trained using Masked Language Modeling on the student essays in the Feedback Prize - Evaluating Student Writing Kaggle Competition. Data is available here: https://www.kaggle.com/c/feedback-prize-2021/data
It achieves the following results on the evaluation set:
- Loss: 1.466
- Accuracy: 0.6834

## Model description

This is google/bigbird-roberta-base trained at 1024 sequence length using Masked Language Modeling pretraining objective on a TPU v3-8

## Intended uses & limitations

In-domain pretraining should help finetuning for the competition.

## Training and evaluation data

Data is a collection of student essays. No modifications made to the files available here: https://www.kaggle.com/c/feedback-prize-2021/data

5% of the files were used as the validation set.

Trained using flax with a [script very similar to this](https://github.com/huggingface/transformers/blob/master/examples/flax/language-modeling/run_mlm_flax.py)

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
```

--model_name_or_path google/bigbird-roberta-base 
--line_by_line 
--validation_split_percentage 5 
--max_seq_length 1024 
--preprocessing_num_workers 40 
--mlm_probability 0.15 
--learning_rate 3e-5 
--weight_decay 0.0095 
--warmup_steps 100 
--num_train_epochs 5 
--dtype float16 
--per_device_train_batch_size 4 
--per_device_eval_batch_size 8 
--logging_steps 50 
--evaluation_strategy steps 
--eval_steps 115 
--save_strategy steps 
--save_steps 115 
--save_total_limit 5 
--seed 18 
```

### Training results

See tensorboard for details: https://huggingface.co/nbroad/feedback-prize-bigbird-base/tensorboard

