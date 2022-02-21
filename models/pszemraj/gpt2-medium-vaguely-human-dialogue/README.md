---
language:
- en
tags:
- text-generation
- gpt2
- gpt
license: mit
datasets:
- natural questions

widget:
- text: "Do you like my new haircut?\nperson beta:\n\n"  
  example_title: "haircut"
- text: "I love to learn new things.. are you willing to teach me something?\nperson beta:\n\n"  
  example_title: "teaching"
- text: "What's your favorite animal? Mine is the dog? \nperson beta:\n\n"
  example_title: "favorite"
- text: "how much does it cost?\nperson beta:\n\n"
  example_title: "money"

inference:
  parameters:
    min_length: 2
    max_length: 64
    length_penalty: 0.6
    no_repeat_ngram_size: 3
    do_sample: True
    top_p: 0.85
    top_k: 10
    repetition_penalty: 2.1
    
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pszemraj/gpt2-medium-vaguely-human-dialogue

This model is a fine-tuned version of [gpt2-medium](https://huggingface.co/gpt2-medium) on a parsed version of Wizard of Wikipedia. Because the batch size was so large, it learned a general understanding of words that makes sense together but does not specifically respond to anything - sort of like an alien learning to imitate human words to convince others that it is human.

It achieves the following results on the evaluation set:
- Loss: 4.3281

## Model description

-  a decent example of what happens when your batch size is too large and the global optima does not reflect specific prompts / use cases.

## Intended uses & limitations

- there are no intended uses


## Training and evaluation data

- a parsed version of the wizard of Wikipedia dataset

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- distributed_type: multi-GPU
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.05
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 34.991        | 1.0   | 837  | 14.8359         |
| 12.2881       | 2.0   | 1674 | 9.375           |
| 8.5071        | 3.0   | 2511 | 7.2148          |
| 7.6031        | 4.0   | 3348 | 6.1758          |
| 6.4808        | 5.0   | 4185 | 5.5820          |
| 5.8562        | 6.0   | 5022 | 5.0977          |
| 5.6094        | 7.0   | 5859 | 4.8203          |
| 5.2591        | 8.0   | 6696 | 4.5977          |
| 5.0031        | 9.0   | 7533 | 4.4219          |
| 4.8837        | 10.0  | 8370 | 4.3281          |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Tokenizers 0.11.0
