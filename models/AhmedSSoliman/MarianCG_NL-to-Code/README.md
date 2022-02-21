---
widget:
- text: "create array containing the maximum value of respective elements of array `[2, 3, 4]` and array `[1, 5, 2]"
- text: "check if all elements in list `mylist` are identical"
- text: "enable debug mode on flask application `app`"
- text: "getting the length of `my_tuple`"
- text: 'find all files in directory "/mydir" with extension ".txt"'
---

# MarianCG: A TRANSFORMER MODEL FOR AUTOMATIC CODE GENERATION
This model is to improve the solving of the code generation problem and implement a transformer model that can work with high accurate results. We implemented MarianCG transformer model which is a code generation model that can be able to generate code from natural language. This work declares the impact of using Marian machine translation model for solving the problem of code generation. In our implementation we prove that a machine translation model can be operated and working as a code generation model.Finally, we set the new contributors and state-of-the-art on CoNaLa reaching a BLEU score of 30.92 in the code generation problem with CoNaLa dataset.

CoNaLa Dataset for Code Generation is available at
https://huggingface.co/AhmedSSoliman/CoNaLa

This is the model is avialable on the huggingface hub https://huggingface.co/AhmedSSoliman/MarianCG_NL-to-Code
```python
# Model and Tokenizer
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
# model_name = "AhmedSSoliman/MarianCG_NL-to-Code"
model = AutoModelForSeq2SeqLM.from_pretrained("AhmedSSoliman/MarianCG_NL-to-Code")
tokenizer = AutoTokenizer.from_pretrained("AhmedSSoliman/MarianCG_NL-to-Code")
# Input (Natural Language) and Output (Python Code)
NL_input = "create array containing the maximum value of respective elements of array `[2, 3, 4]` and array `[1, 5, 2]"
output = model.generate(**tokenizer(NL_input, padding="max_length", truncation=True, max_length=512, return_tensors="pt"))
output_code = tokenizer.decode(output[0], skip_special_tokens=True)
```

This model is available in spaces using gradio at: https://huggingface.co/spaces/AhmedSSoliman/MarianCG_NL-to-Code


---
Tasks:
- Translation
- Code Generation
- Text2Text Generation
- Text Generation
---