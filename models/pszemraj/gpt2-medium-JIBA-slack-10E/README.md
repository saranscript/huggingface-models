---
language:
- en
tags:
- text-generation
- gpt2
- gpt2-medium
datasets:
- JIBA-slack

widget:
- text: "I am the best, my sister is the worst. What am I?\n" 
  example_title: "sister"
- text: "What do you call an alligator who's just had surgery to remove his left arm?\n" 
  example_title: "alligator"
- text: "A man walks into a bar and asks for a drink. The bartender asks for $10 and he pays him $1. What did he pay him with?\n" 
  example_title: "dollar"
- text: "What did I say was in the mailbox, when it was actually in the cabinet?\n" 
  example_title: "mailbox"
- text: "My friend says that she knows every language, but she doesn't speak any of them.. what's wrong with her?\n" 
  example_title: "language"
- text: "I know you're tired, but can we go for another walk this evening?\n" 
  example_title: "walk"
- text: "Omg how are you doing??\n" 
  example_title: "small talk"
- text: "What is the name of the famous author of The Great Gatsby?\n" 
  example_title: "author"
- text: "What is the name of the last Wal-Mart Superstore in Canada?\n" 
  example_title: "walmart"
- text: "I don't understand why people like this so much. I'd rather drink milk. What do you think?\n" 
  example_title: "beer"
- text: "My wife only has two hobbies, and one of them is collecting bottle caps.. what's her other hobby?\n" 
  example_title: "hobby"
- text: "My first is in Asia, my second is in Europe, my third is in North America, and my fourth is in South America. What am I?\n"
  example_title: "continent"
- text: "Can you actually take me for dinner somewhere nice this time?\n"
  example_title: "dinner"
- text: "Honey, I have clogged the toilet for the third time this month.. sorry..\n"
  example_title: "overflow"
- text: "A man pushes his car to a hotel and tells the owner he’s bankrupt. Why?\n"
  example_title: "brain teaser"
  
inference:
  parameters:
    min_length: 2
    max_length: 64
    length_penalty: 0.5
    no_repeat_ngram_size: 3
    do_sample: True
    top_p: 0.95
    top_k: 30
    repetition_penalty: 3.5
    

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# gpt2-medium-JIBA_DS-slack-chat_Ep-10_Bs-32

This model is a fine-tuned version of [gpt2-medium](https://huggingface.co/gpt2-medium) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 7.8711

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.001
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- distributed_type: multi-GPU
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_ratio: 0.05
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 0.99  | 40   | 48.5            |
| No log        | 1.99  | 80   | 21.9375         |
| No log        | 2.99  | 120  | 12.9297         |
| No log        | 3.99  | 160  | 11.7734         |
| No log        | 4.99  | 200  | 9.9453          |
| No log        | 5.99  | 240  | 9.4219          |
| No log        | 6.99  | 280  | 9.1875          |
| No log        | 7.99  | 320  | 8.3516          |
| No log        | 8.99  | 360  | 7.8438          |
| No log        | 9.99  | 400  | 7.8711          |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Tokenizers 0.11.0
