---

language:
- en
tags:
- text-generation
- gpt-neo
- god-mode
license: mit
datasets:
- daily_dialogue

widget:
- text: "I am the best; my sister is the worst. What am I?\npeter szemraj:\n\n" 
  example_title: "sister"
- text: "What do you call an alligator who's just had surgery to remove his left arm?\npeter szemraj:\n\n" 
  example_title: "alligator"
- text: "A man walks into a bar and asks for a drink. The bartender asks for $10, and he pays him $1. What did he pay him with?\npeter szemraj:\n\n" 
  example_title: "dollar"
- text: "What did I say was in the mailbox when it was actually in the cabinet?\npeter szemraj:\n\n" 
  example_title: "mailbox"
- text: "My friend says that she knows every language, but she doesn't speak any of them.. what's wrong with her?\npeter szemraj:\n\n." 
  example_title: "language"
- text: "I know you're tired, but can we go for another walk this evening?\npeter szemraj:\n\n" 
  example_title: "walk"
- text: "I have two daughters. The older one is married to a doctor, and the younger one is married to a lawyer. What is the name of my son-in-law?\npeter szemraj:\n\n"
  example_title: "riddle"
- text: "My first is in Asia, my second is in Europe, my third is in North America, and my fourth is in South America. What am I?\npeter szemraj:\n\n"
  example_title: "continent"
- text: "Can you take me for dinner somewhere nice this time?\npeter szemraj:\n\n"
  example_title: "dinner"
- text: "Honey, I have clogged the toilet for the third time this month.. sorry..\npeter szemraj:\n\n"
  example_title: "overflow"
- text: "A man pushes his car to a hotel and tells the owner he's bankrupt. Why?\npeter szemraj:\n\n"
  example_title: "brain teaser"

inference:
  parameters:
    min_length: 2
    max_length: 64
    length_penalty: 0.7
    no_repeat_ngram_size: 3
    do_sample: True
    top_p: 0.90
    top_k: 15
    repetition_penalty: 2.1
    

---
# gpt-neo-125M-Peter: 14 epochs

This model is a fine-tuned version of [EleutherAI/gpt-neo-125M](https://huggingface.co/EleutherAI/gpt-neo-125M) on whatsapp/iMessage dataset of the divine being himself.

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

Message data through Feb 4, Year of Our Lord 2022

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 4e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- distributed_type: multi-GPU
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- num_epochs: 14

### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Tokenizers 0.11.0
