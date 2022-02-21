---
license: apache-2.0
tags:
- generated_from_trainer

widget:
- text: "I know you're tired, but can we go for another walk this evening?\nperson beta:\n\n" 
  example_title: "walk"
- text: "Have you done anything exciting lately?\nperson beta:\n\n"
  example_title: "activities"
- text: "hey - do you have a favourite grocery store around here?\nperson beta:\n\n"
  example_title: "grocery"
- text: "Can you take me for dinner somewhere nice this time?\nperson beta:\n\n"
  example_title: "dinner"
- text: "What's your favorite form of social media?\nperson beta:\n\n"
  example_title: "social media"
- text: "Hi, how are you?\nperson beta:\n\n"
  example_title: "greeting"
- text: "I am the best; my sister is the worst. What am I?\nperson beta:\n\n" 
  example_title: "sister"
- text: "What do you call an alligator who's just had surgery to remove his left arm?\nperson beta:\n\n" 
  example_title: "alligator"
- text: "A man walks into a bar and asks for a drink. The bartender asks for $10, and he pays him $1. What did he pay him with?\nperson beta:\n\n" 
  example_title: "dollar"
- text: "What did I say was in the mailbox when it was actually in the cabinet?\nperson beta:\n\n" 
  example_title: "mailbox"
- text: "My friend says that she knows every language, but she doesn't speak any of them.. what's wrong with her?\nperson beta:\n\n." 
  example_title: "language"

inference:
  parameters:
    min_length: 2
    max_length: 64
    length_penalty: 0.7
    no_repeat_ngram_size: 2
    do_sample: True
    top_p: 0.95
    top_k: 30
    repetition_penalty: 2.1
    
---


# distilgpt2-tiny-conversational

This model is a fine-tuned version of [distilgpt2](https://huggingface.co/distilgpt2) on a parsed version of Wizard of Wikipedia. Persona alpha/beta framework designed for use with [ai-msgbot](https://github.com/pszemraj/ai-msgbot).
It achieves the following results on the evaluation set:
- Loss: 2.2461

## Model description

- it is a splendid model

## Intended uses & limitations

- [ai-msgbot](https://github.com/pszemraj/ai-msgbot)

## Training and evaluation data

- [wizard of Wikipedia](https://parl.ai/projects/wizard_of_wikipedia/) parsed, from parlAI

## Training procedure

- deepspeed + huggingface trainer, an example notebook is in [ai-msgbot](https://github.com/pszemraj/ai-msgbot)

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- distributed_type: multi-GPU
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.05
- num_epochs: 30

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| No log        | 1.0   | 418   | 2.7793          |
| 2.9952        | 2.0   | 836   | 2.6914          |
| 2.7684        | 3.0   | 1254  | 2.6348          |
| 2.685         | 4.0   | 1672  | 2.5938          |
| 2.6243        | 5.0   | 2090  | 2.5625          |
| 2.5816        | 6.0   | 2508  | 2.5332          |
| 2.5816        | 7.0   | 2926  | 2.5098          |
| 2.545         | 8.0   | 3344  | 2.4902          |
| 2.5083        | 9.0   | 3762  | 2.4707          |
| 2.4793        | 10.0  | 4180  | 2.4551          |
| 2.4531        | 11.0  | 4598  | 2.4395          |
| 2.4269        | 12.0  | 5016  | 2.4238          |
| 2.4269        | 13.0  | 5434  | 2.4102          |
| 2.4051        | 14.0  | 5852  | 2.3945          |
| 2.3777        | 15.0  | 6270  | 2.3848          |
| 2.3603        | 16.0  | 6688  | 2.3711          |
| 2.3394        | 17.0  | 7106  | 2.3613          |
| 2.3206        | 18.0  | 7524  | 2.3516          |
| 2.3206        | 19.0  | 7942  | 2.3398          |
| 2.3026        | 20.0  | 8360  | 2.3301          |
| 2.2823        | 21.0  | 8778  | 2.3203          |
| 2.2669        | 22.0  | 9196  | 2.3105          |
| 2.2493        | 23.0  | 9614  | 2.3027          |
| 2.2334        | 24.0  | 10032 | 2.2930          |
| 2.2334        | 25.0  | 10450 | 2.2852          |
| 2.2194        | 26.0  | 10868 | 2.2754          |
| 2.2014        | 27.0  | 11286 | 2.2695          |
| 2.1868        | 28.0  | 11704 | 2.2598          |
| 2.171         | 29.0  | 12122 | 2.2539          |
| 2.1597        | 30.0  | 12540 | 2.2461          |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Tokenizers 0.11.0
