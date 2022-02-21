---
Language Pair Finetuned:
- en-mr

Metrics:
- sacrebleu
  - WAT 2021: 16.11

# mbart-large-finetuned-en-mr
 
## Model Description
 This is the mbart-large-50 model finetuned on En-Mr corpus.
  
## Intended uses and limitations
 Mostly useful for English to Marathi translation but the mbart-large-50 model also supports other language pairs
 
### How to use
```python
from transformers import MBartForConditionalGeneration, MBart50TokenizerFast

model = MBartForConditionalGeneration.from_pretrained("shivam/mbart-large-50-finetuned-en-mr")
tokenizer = MBart50TokenizerFast.from_pretrained("shivam/mbart-large-50-finetuned-en-mr", src_lang="en_XX", tgt_lang="mr_IN")

english_input_sentence = "The Prime Minister said that cleanliness, or Swachhta, is one of the most important aspects of preventive healthcare."
model_inputs = tokenizer(english_input_sentence, return_tensors="pt")
generated_tokens = model.generate(
    **model_inputs,
    forced_bos_token_id=tokenizer.lang_code_to_id["mr_IN"]
)
marathi_output_sentence = tokenizer.batch_decode(generated_tokens, skip_special_tokens=True)

print(marathi_output_sentence)
#स्वच्छता हा प्रतिबंधात्मक आरोग्य सेवेतील सर्वात महत्त्वाचा पैलू आहे, असे पंतप्रधान म्हणाले.
```
#### Limitations
 The model was trained on Google Colab and as the training takes a lot of time the model was trained for small time and small number of epochs.

## Eval results 
 WAT 2021: 16.11 