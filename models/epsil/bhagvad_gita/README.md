This is fine-tuned model on Bhagvad Gita and creates text based on prompts.
Example of usage:

```
from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("epsil/bhagvad_gita")

model = AutoModelForCausalLM.from_pretrained("epsil/bhagvad_gita")

```
Input
```
from transformers import pipeline

pipeline = pipeline('text-generation',model=model, tokenizer=tokenizer)

result = samples('Krishna show me the right path')[0]['generated_text']
print(result)

```

Output
```
Krishna show me the right path, and I also to remember the lessons, and to remember them right.

Sama! in His Day, and by Thy own Eternal Grace.

A man like that who shall come to us

```

> Created by [Saurabh Mishra](https://www.linkedin.com/in/saurabh-mishra-12b5a1216/)

> Made with <span style="color: #e25555;">&hearts;</span> in India

