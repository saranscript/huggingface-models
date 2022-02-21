# GPT-Code-Clippy-125M-Code-Search-All
> **Please refer to our new [GitHub Wiki](https://github.com/ncoop57/gpt-code-clippy/wiki) which documents our efforts in detail in creating the open source version of GitHub  Copilot**


## Model Description

GPT-CC-125M-Code-Search is a [GPT-Neo-125M model](https://huggingface.co/EleutherAI/gpt-neo-125M) finetuned using causal language modeling on all languages in the [CodeSearchNet Challenge dataset](https://huggingface.co/datasets/code_search_net). This model is specialized to autocomplete methods in multiple programming languages.

## Training data

[CodeSearchNet Challenge dataset](https://huggingface.co/datasets/code_search_net).

## Training procedure

The training script used to train this model can be found [here](https://github.com/ncoop57/gpt-code-clippy/blob/camera-ready/training/run_clm_flax.py).

```bash
./run_clm_flax.py \
    --output_dir $HOME/gpt-neo-125M-code-search-all \
    --model_name_or_path="EleutherAI/gpt-neo-125M" \
    --dataset_name code_search_net \
    --dataset_config_name="all" \
    --do_train --do_eval \
    --block_size="512" \
    --per_device_train_batch_size="32" \
    --per_device_eval_batch_size="64" \
    --preprocessing_num_workers="8" \
    --learning_rate="1.2e-4" \
    --num_train_epochs 20 \
    --warmup_steps 3000 \
    --adam_beta1="0.9" \
    --adam_beta2="0.95" \
    --weight_decay="0.1" \
    --overwrite_output_dir \
    --logging_steps="25" \
    --eval_steps="500" \
    --push_to_hub="False" \
    --report_to="all" \
    --dtype="bfloat16" \
    --skip_memory_metrics="True" \
    --save_steps="500" \
    --save_total_limit 10 \
    --report_to="wandb" \
    --run_name="gpt-neo-125M-code-search-all"
```

## Intended Use and Limitations

The model is finetuned methods from several languages and is intended to autocomplete methods given some prompt (method signature and docstring).

### How to use

You can use this model directly with a pipeline for text generation. This example generates a different sequence each time it's run:

```py

from transformers import AutoModelForCausalLM, AutoTokenizer, FlaxAutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained("flax-community/gpt-neo-125M-code-clippy-code-search-all")

tokenizer = AutoTokenizer.from_pretrained("flax-community/gpt-neo-125M-code-clippy-code-search-all")

prompt = """def greet(name):
  '''A function to greet user. Given a user name it should say hello'''
""" 

input_ids = tokenizer(prompt, return_tensors='pt').input_ids.to(device)

start = input_ids.size(1)

out = model.generate(input_ids, do_sample=True, max_length=50, num_beams=2, 

                     early_stopping=True, eos_token_id=tokenizer.eos_token_id, )

print(tokenizer.decode(out[0][start:]))

```

### Limitations and Biases

The model is intended to be used for research purposes and comes with no guarantees of quality of generated code.

GPT-CC is finetuned from GPT-Neo and might have inherited biases and limitations from it. See [GPT-Neo model card](https://huggingface.co/EleutherAI/gpt-neo-125M#limitations-and-biases) for details.

## Eval results

Coming soon...