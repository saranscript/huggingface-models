# ByT5 Dutch OCR Correction 

This model is a finetuned byT5 model that corrects OCR mistakes found in dutch sentences. The [google/byt5-base](https://huggingface.co/google/byt5-base) model is finetuned on the dutch section of the [OSCAR](https://huggingface.co/datasets/oscar) dataset. 


## Usage

```python
from transformers import AutoTokenizer, T5ForConditionalGeneration

example_sentence = "Ben algoritme dat op ba8i8 van kunstmatige inte11i9entie vkijwel geautomatiseerd een tekst herstelt met OCR fuuten."

tokenizer = AutoTokenizer.from_pretrained('ml6team/byt5-base-dutch-ocr-correction')

model_inputs = tokenizer(example_sentence, max_length=128, truncation=True, return_tensors="pt")

model = T5ForConditionalGeneration.from_pretrained('ml6team/byt5-base-dutch-ocr-correction')
outputs = model.generate(**model_inputs, max_length=128)

tokenizer.decode(outputs[0])
```