# GPT-Code-Clippy-125M-from-Scratch
> **Please refer to our new [GitHub Wiki](https://github.com/ncoop57/gpt-code-clippy/wiki) which documents our efforts in detail in creating the open source version of GitHub  Copilot**
## Model Description

GPT-CC-125M-from-Scratch is a [GPT-Neo-125M model](https://huggingface.co/EleutherAI/gpt-neo-125M) pretrained from scratch using causal language modeling on the [Code Clippy Post-deduplication dataset](https://the-eye.eu/public/AI/training_data/code_clippy_data/code_clippy_dedup_data/). The deduplication script can be found [here](https://github.com/ncoop57/gpt-code-clippy/blob/camera-ready/data_processing/deduplication/deduplication.py). Code Clippy was scraped from public Github repositories (more information in the provided link). This model is specialized to autocomplete methods in multiple programming languages. As discussed in OpenAI's [Codex paper](https://arxiv.org/abs/2107.03374), we modified the GPT-Neo model and tokenizer to accommodate for additional whitespace characters. Specifically, we add the following tokens `["\t\t", "  ", "    ", "        "]` and since they are all related to indentation, we initialize the embedding layer of these tokens with the same weights as the `\t` token already present in the model in hopes the model will learn to associate these whitespace characters with indentation faster. A script to automatically do this can be found [here](https://github.com/ncoop57/gpt-code-clippy/blob/camera-ready/training/utilities/add_new_tokens.py).

## Training data

[Code Clippy Deduplicated dataset](https://the-eye.eu/public/AI/training_data/code_clippy_data/code_clippy_dedup_data/).
Python script of the dataset can be found [here](https://github.com/ncoop57/gpt-code-clippy/blob/camera-ready/data_processing/code_clippy.py)

## Training procedure

The training script used to train this model can be found [here](https://github.com/ncoop57/gpt-code-clippy/blob/camera-ready/training/deprecated/run_clm_streaming_flax_v2.py).

```bash
./run_clm_streaming_flax_v2.py \
    --output_dir $HOME/gpt-neo-125M-code-clippy-from-scratch \
     --tokenizer_name="EleutherAI/gpt-neo-125M" \
    --model_name_or_path="EleutherAI/gpt-neo-125M" \
    --dataset_name $HOME/gpt-code-clippy/data_processing/code_clippy.py \
    --data_dir /home/shared/code_clippy_data \
    --do_train --do_eval \
    --block_size="2048" \
    --per_device_train_batch_size="8" \
    --per_device_eval_batch_size="16" \
    --preprocessing_num_workers="8" \
    --learning_rate="3e-5" \
    --max_steps 100000 \
    --warmup_steps 2500\
    --decap_steps 25000 \
    --adam_beta1="0.9" \
    --adam_beta2="0.95" \
    --weight_decay="0.1" \
    --overwrite_output_dir \
    --logging_steps="50" \
    --eval_steps="500" \
    --push_to_hub="False" \
    --report_to="all" \
    --dtype="bfloat16" \
    --skip_memory_metrics="True" \
    --save_steps="500" \
    --save_total_limit 10 \
    --report_to="wandb" \
    --run_name="gpt-neo-125M-code-clippy-dedup-scratch"
```

## Intended Use and Limitations

The model is pre-trained and not finetuned for any particular use or a particular programming language. Due to time constraints, this model was only pre-trained on 1% of the Code Clippy Dataset.


The paper ["Evaluating Large Language Models Trained on Code"](https://arxiv.org/abs/2107.03374) from OpenAI has a good discussion on what the impact of a large language model trained on code could be. Therefore, some parts of their discuss are highlighted here as it pertains to this dataset and models that may be trained from it. **As well as some differences in views from the paper, particularly around legal implications**.

1. **Over-reliance:** This model may generate plausible solutions that may appear correct, but are not necessarily the correct solution. Not properly evaluating the generated code may cause have negative consequences such as the introduction of bugs, or the introduction of security vulnerabilities. Therefore, it is important that users are aware of the limitations and potential negative consequences of using this language model.
2. **Economic and labor market impacts:** Large language models trained on large code datasets such as this one that are capable of generating high-quality code have the potential to automate part of the software development process. This may negatively impact software developers. However, as discussed in the paper, as shown in the Summary Report of software developers from [O*NET OnLine](https://www.onetonline.org/link/summary/15-1252.00), developers don't just write software.
3. **Security implications:** No filtering or checking of vulnerabilities or buggy code was performed on the datase this model is trained on. This means that the dataset may contain code that may be malicious or contain vulnerabilities. Therefore, this model may generate vulnerable, buggy, or malicious code. In safety critical software, this could lead to software that may work improperly and could result in serious consequences depending on the software. Additionally, this model may be able to be used to generate malicious code on purpose in order to perform ransomware or other such attacks.
4. **Legal implications:** No filtering was performed on licensed code. This means that the dataset may contain restrictive licensed code. As discussed in the paper, public Github repositories may fall under "fair use." However, there has been little to no previous cases of such usages of licensed publicly available code. Therefore, any code generated with this model may be required to obey license terms that align with the software it was trained on such as GPL-3.0. It is unclear the legal ramifications of using a language model trained on this dataset.
5. **Biases:** The programming languages most represented in the dataset this model was trained on are Javascript and Python. Therefore, other, still popular languages such as C and C++, are less represented and therefore the models performance for these languages will be less comparatively. Additionally, this dataset only contains public repositories and so the model may not generate code that is representative of code written by private developers. No filtering was performed for potential racist, offensive, or otherwise inappropriate content. Therefore, this model may reflect such biases in its generation.

GPT-Neo-125M-Code-Clippy is finetuned from GPT-Neo and might have inherited biases and limitations from it. See [GPT-Neo model card](https://huggingface.co/EleutherAI/gpt-neo-125M#limitations-and-biases) for details.

### How to use

You can use this model directly with a pipeline for text generation. This example generates a different sequence each time it's run:

```py

from transformers import AutoModelForCausalLM, AutoTokenizer, FlaxAutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained("flax-community/gpt-neo-125M-code-clippy-dedup-scratch")

tokenizer = AutoTokenizer.from_pretrained("flax-community/gpt-neo-125M-code-clippy-dedup-scratch")

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

The model is intended to be used for research purposes and comes with no guarantees of the quality of generated code.

GPT-CC is finetuned from GPT-Neo and might have inherited biases and limitations from it. See [GPT-Neo model card](https://huggingface.co/EleutherAI/gpt-neo-125M#limitations-and-biases) for details.

## Evaluation results
Below is a table containing the base model we started from, and the model's performance on the [HumanEval Benchmark](https://github.com/openai/human-eval).

|    Model     |    Dataset Used     |   pass@1    |   pass@2    |   pass@5    |   pass@10   |
|     ---      |          ---        | :---------: | :---------: | :---------: | :---------: |
| [gpt-neo-125M (**trained from scratch**)](https://huggingface.co/flax-community/gpt-neo-125M-code-clippy-dedup-scratch) |  [Code Clippy Data (Deduplicated)](https://the-eye.eu/public/AI/training_data/code_clippy_data/code_clippy_dedup_data/) (~1% of the data)  |    0.00%    |    0.00%    |    0.00%    |    0.00%    |