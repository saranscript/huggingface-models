---
language: 
  - fr
tags:
- text-generation
license: mit
datasets:
- oscar
widget:
- text: "Je suis ravi de vous "
---

# GPT-2 finetuned on French Dataset

### Tokenizer
We use GPT-2 tokenizer.

### Model
We finetuned the `wte` and `wpe` layers of GPT-2 (while freezing the parameters of all other layers) on OSCAR's `unshuffled_original_fr` French data subset. We used [Huggingface's code](https://github.com/huggingface/transformers/blob/master/examples/pytorch/language-modeling/run_clm.py) for fine-tuning the causal language model GPT-2, but with the following parameters changed
```
- preprocessing_num_workers: 8
- per_device_train_batch_size: 2
- gradient_accumulation_steps: 4
- per_device_eval_batch_size: 2
- eval_accumulation_steps: 4
- eval_steps: 1000 
- evaluation_strategy: "steps"
- max_eval_samples: 5000
```

**Final checkpoint**: checkpoint-76500