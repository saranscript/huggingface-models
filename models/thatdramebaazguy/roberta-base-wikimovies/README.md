---
datasets:
- wikimovies

language: 
- English

thumbnail: 

tags:
- roberta
- roberta-base
- masked-language-modeling 

license: cc-by-4.0

---
# roberta-base for MLM 

```
model_name = "thatdramebaazguy/roberta-base-wikimovies"
pipeline(model=model_name, tokenizer=model_name, revision="v1.0", task="Fill-Mask")
```
## Overview
**Language model:** roberta-base  
**Language:** English  
**Downstream-task:** Fill-Mask  
**Training data:** wikimovies  
**Eval data:** wikimovies  
**Infrastructure**: 2x Tesla v100   
**Code:**  See [example](https://github.com/adityaarunsinghal/Domain-Adaptation/blob/master/shell_scripts/train_movie_roberta.sh)    

## Hyperparameters
```
num_examples = 4346
batch_size = 16
n_epochs = 3
base_LM_model = "roberta-base"
learning_rate = 5e-05
max_query_length=64
Gradient Accumulation steps = 1
Total optimization steps = 816
evaluation_strategy=IntervalStrategy.NO
prediction_loss_only=False
per_device_train_batch_size=8
per_device_eval_batch_size=8
adam_beta1=0.9
adam_beta2=0.999
adam_epsilon=1e-08,
max_grad_norm=1.0
lr_scheduler_type=SchedulerType.LINEAR
warmup_ratio=0.0
seed=42
eval_steps=500
metric_for_best_model=None
greater_is_better=None
label_smoothing_factor=0.0
``` 
## Performance

perplexity = 4.3808

Some of my work: 
- [Domain-Adaptation Project](https://github.com/adityaarunsinghal/Domain-Adaptation/)

---
