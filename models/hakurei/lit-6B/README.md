---
language:
- en
tags:
- pytorch
- causal-lm
license: mit

---

# Lit-6B - A Large Fine-tuned Model For Fictional Storytelling

Lit-6B is a GPT-J 6B model fine-tuned on 2GB of a diverse range of light novels, erotica, and annotated literature for the purpose of generating novel-like fictional text. 

## Model Description

The model used for fine-tuning is [GPT-J](https://github.com/kingoflolz/mesh-transformer-jax), which is a 6 billion parameter auto-regressive language model trained on [The Pile](https://pile.eleuther.ai/).

## Training Data & Annotative Prompting

The data used in fine-tuning has been gathered from various sources such as the [Gutenberg Project](https://www.gutenberg.org/). The annotated fiction dataset has prepended tags to assist in generating towards a particular style. Here is an example prompt that shows how to use the annotations.

```
[ Title: The Dunwich Horror; Author: H. P. Lovecraft; Genre: Horror; Tags: 3rdperson, scary; Style: Dark ]
***
When a traveler in north central Massachusetts takes the wrong fork...
```

The annotations can be mixed and matched to help generate towards a specific style.

## Downstream Uses

This model can be used for entertainment purposes and as a creative writing assistant for fiction writers.

## Example Code

```
from transformers import AutoTokenizer, AutoModelForCausalLM

model = AutoModelForCausalLM.from_pretrained('hakurei/lit-6B')
tokenizer = AutoTokenizer.from_pretrained('hakurei/lit-6B')

prompt = '''[ Title: The Dunwich Horror; Author: H. P. Lovecraft; Genre: Horror ]
***
When a traveler'''

input_ids = tokenizer.encode(prompt, return_tensors='pt')
output = model.generate(input_ids, do_sample=True, temperature=1.0, top_p=0.9, repetition_penalty=1.2, max_length=len(input_ids[0])+100, pad_token_id=tokenizer.eos_token_id)

generated_text = tokenizer.decode(output[0])
print(generated_text)
```

An example output from this code produces a result that will look similar to:

```
[ Title: The Dunwich Horror; Author: H. P. Lovecraft; Genre: Horror ]
***
When a traveler comes to an unknown region, his thoughts turn inevitably towards the old gods and legends which cluster around its appearance. It is not that he believes in them or suspects their reality—but merely because they are present somewhere else in creation just as truly as himself, and so belong of necessity in any landscape whose features cannot be altogether strange to him. Moreover, man has been prone from ancient times to brood over those things most connected with the places where he dwells. Thus the Olympian deities who ruled Hyper
```

## Team members and Acknowledgements

This project would not have been possible without the computational resources graciously provided by the [TPU Research Cloud](https://sites.research.google/trc/)

- [Anthony Mercurio](https://github.com/harubaru)
- Imperishable_NEET