---
language:
- en
- python
license: mit
tags:
- gpt_neo
- code_synthesis
datasets:
- apps
---

# GPT-Neo-125M-APPS
> **Please refer to our new [GitHub Wiki](https://github.com/ncoop57/gpt-code-clippy/wiki) which documents our efforts in detail in creating the open source version of GitHub  Copilot**

## Model Description

GPT-Neo-125M-APPS is a GPT-Neo-125M finetuned on APPS dataset. This model is specialized to solve programming tasks.

## Training data

The model is trained on the [Automated Programming Progress Standard (APPS) dataset](https://github.com/hendrycks/apps). The dataset consists of 10,000 coding problems in total, with 131,836 test cases for checking solutions and 232,444 ground-truth solutions written by humans. Problems can be complicated, as the average length of a problem is 293.2 words. The data are split evenly into training and test sets, with 5,000 problems each.


## Training procedure

The training script used to train this model can be found [here](https://github.com/ncoop57/gpt-code-clippy/blob/camera-ready/training/run_clm_apps.py).

Training is done for 5 epochs using AdamW optimizer and leaner decay learning rate schedule with 800 warmup steps. To reproduce the training one can use this command with the above script:

```bash
python run_clm_apps.py \
    --output_dir $HOME/gpt-neo-125M-apps \
    --model_name_or_path EleutherAI/gpt-neo-125M \
    --dataset_name $HOME/gpt-code-clippy/data_processing/apps.py \
    --dataset_config_name formatted \
    --do_train --do_eval \
    --block_size="1024" \
    --per_device_train_batch_size="16" \
    --per_device_eval_batch_size="16" \
    --preprocessing_num_workers="16" \
    --learning_rate="8e-5" \
    --warmup_steps="800" \
    --adam_beta1="0.9" \
    --adam_beta2="0.98" \
    --weight_decay="0.1" \
    --overwrite_output_dir \
    --num_train_epochs="5" \
    --logging_steps="50" \
    --eval_steps="2000" \
    --report_to="wandb" \
    --dtype="bfloat16" \
    --save_strategy epoch \
    --gradient_accumulation_steps 2 \

```

## Intended Use and Limitations

The model is finetuned to solve programming problems given a text description and optional starter code.

### How to use

You can use this model directly with a pipeline for text generation. This example generates a different sequence each time it's run:

```py
from transformers import AutoModelForCausalLM, AutoTokenizer, FlaxAutoModelForCausalLM
model = AutoModelForCausalLM.from_pretrained("flax-community/gpt-neo-125M-apps")
tokenizer = AutoTokenizer.from_pretrained("flax-community/gpt-neo-125M-apps")

prompt = """
A function to greet user. Given a user name it should say hello
def greet(name):
ANSWER:
""" 

input_ids = tokenizer(prompt, return_tensors='pt').input_ids.to(device)
start = input_ids.size(1)
out = model.generate(input_ids, do_sample=True, max_length=50, num_beams=2, 
                     early_stopping=True, eos_token_id=tokenizer.eos_token_id, )
print(tokenizer.decode(out[0][start:]))
```

### Limitations and Biases

The model is intended to be used for research purposes and comes with no guarantees of quality of generated code.

The paper ["Evaluating Large Language Models Trained on Code"](https://arxiv.org/abs/2107.03374) from OpenAI has a good discussion on what the impact of a large language model trained on code could be. Therefore, some parts of their discuss are highlighted here as it pertains to this dataset and models that may be trained from it. **As well as some differences in views from the paper, particularly around legal implications**.

1. **Over-reliance:** This model may generate plausible solutions that may appear correct, but are not necessarily the correct solution. Not properly evaluating the generated code may cause have negative consequences such as the introduction of bugs, or the introduction of security vulnerabilities. Therefore, it is important that users are aware of the limitations and potential negative consequences of using this language model.

2. **Economic and labor market impacts:** Large language models trained on large code datasets such as this one that are capable of generating high-quality code have the potential to automate part of the software development process. This may negatively impact software developers. However, as discussed in the paper, as shown in the Summary Report of software developers from [O*NET OnLine](https://www.onetonline.org/link/summary/15-1252.00), developers don't just write software.

5. **Biases:** The model is trained on data containing prompt questions formatted in specific way. The performance of the model can be worse if the prompt 

formatting is different from that used in APPS dataset.

GPT-CC is finetuned GPT-Neo and might have inhereted biases and limitations from it. See [GPT-Neo model card](https://huggingface.co/EleutherAI/gpt-neo-125M#limitations-and-biases) for details.

## Eval results

Coming soon...

