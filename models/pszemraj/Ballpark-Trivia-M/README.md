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
- text: "how many ping-pong balls fit inside a standard 747 jet aeroplane?\nperson beta:\n\n"
  example_title: "ping-pong"
- text: "What is the capital of Uganda?\nperson beta:\n\n"
  example_title: "geography"
- text: "What is the most popular TV show of all time?\nperson beta:\n\n"
  example_title: "pseudo-culture"
- text: "A man pushes his car to a hotel and tells the owner he’s bankrupt. Why?\nperson beta:\n\n"
  example_title: "brain teaser"

inference:
  parameters:
    min_length: 2
    max_length: 32
    no_repeat_ngram_size: 2
    do_sample: True
    top_p: 0.90
    top_k: 10


---
# Ballpark Trivia: Size M

Are you frequently asked google-able Trivia questions and annoyed by it? Well, this is the model for you! Ballpark Trivia Bot answers any trivia question with something that sounds plausible but is probably not 100% correct. One might say.. the answers are in the right ballpark. 

> The size M is smaller and less capable but loads _a lot_ faster. The inference API does not like size M for some reason, [here](https://colab.research.google.com/gist/pszemraj/e2c5cee3361122d878062d0287ebc799/scratchpad.ipynb) is a Colab gist to test it out.

## Training 
This text gen model is a GPT-2 ~350 M Parameter Size M Model, trained for 40k steps on a parsed variant of [Natural Questions](https://ai.google.com/research/NaturalQuestions)(with **22**/24 layers frozen for the fine-tuning) to create this model accidentally. 


Note that because the model was originally trained for use in a [chatbot application](https://github.com/pszemraj/ai-msgbot), it uses a named conversation dialogue structure, _, i.e. the questions are asked by person alpha, and responded to by person beta_. Even if you don't specify person alpha in the prompt, it hopefully responds to any question.

## Example Prompt

```
when was the french revolution?

person beta: 
1805
```

- the provided examples are not great
- you can type in any trivia question or delete the example and write `what`  or `when` in there, and it will generate the rest of the trivia question **and the answer**!



