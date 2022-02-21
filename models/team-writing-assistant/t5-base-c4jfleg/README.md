# Model Description:
To create t5-base-c4jfleg model, T5-base model is fine-tuned on the [**JFLEG dataset**](https://huggingface.co/datasets/jfleg) and [**C4 200M dataset**](https://huggingface.co/datasets/liweili/c4_200m) by taking around 3000 examples from each with the objective of grammar correction.


The original Google's [**T5-base**] model was pre-trained on [**C4 dataset**](https://huggingface.co/datasets/c4).

The T5 model was presented in [**Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer**](https://arxiv.org/pdf/1910.10683.pdf) by Colin Raffel, Noam Shazeer, Adam Roberts, Katherine Lee, Sharan Narang, Michael Matena, Yanqi Zhou, Wei Li, Peter J. Liu.

# Prefix:
The T-5 model use "grammar: " as the input text prefix for grammatical corrections.

## Usage :
```
from transformers import pipeline

checkpoint = "team-writing-assistant/t5-base-c4jfleg"
model = pipeline("text2text-generation", model=checkpoint)

text = "Speed of light is fastest then speed of sound"
text = "grammar: " + text

output = model(text)
print("Result: ", output[0]['generated_text'])
```
```
Result: Speed of light is faster than speed of sound.
```

## Other Examples :
Input: My grammar are bad.   
Output: My grammar is bad.

Input: Who are the president?   
Output: Who is the president?