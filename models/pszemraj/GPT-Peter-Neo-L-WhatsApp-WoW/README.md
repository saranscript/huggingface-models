---

language:
- en
tags:
- text-generation
- gpt-neo
- 1.3B
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

# GPT-Peter

A text generation model that consists of the following:

1. trained GPT-Neo 1.3 B checkpoint
2. fine-tune on Parl AI [Wizard of Wikipedia](https://parl.ai/projects/wizard_of_wikipedia/) for 10 epochs  - this checkpoint is [here](https://huggingface.co/pszemraj/gpt-neo-1pt3B-Conv_DS-WoW_Ep-10_Bs-16)
3. fine-tune on WhatsApp messages (mine) for three epochs

# example

## prompt to inference API

`My name is Thomas and my`

## output of inference API

```
My name is Thomas and my main hobby is raising seals

peter szemraj:
hey man my friend had to deal with this, no word one way or the other from our end
```

# PSA

please use my AI cloned person responsibly, danke

