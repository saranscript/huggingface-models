---
language: 
- en
tags:
- generation
- math learning
- education
license: mit
metrics:
- PerspectiveAPI
widget:
- text: "<bos><speaker1>Hello! My name is CL. Nice meeting y'all!<speaker2>[SAFE]"
  example_title: "Safe Response"
- text: "<bos><speaker1>Hello! My name is CL. Nice meeting y'all!<speaker2>[UNSAFE]"
  example_title: "Unsafe Response"
---

# Math-RoBERTa for NLP tasks in math learning environments

This model is fine-tuned with GPT2-xl with 8 Nvidia RTX 1080Ti GPUs and enhanced with conversation safety policies (e.g., threat, profanity, identity attack) using 3,000,000 math discussion posts by students and facilitators on Algebra Nation (https://www.mathnation.com/). SafeMathBot consists of 48 layers and over 1.5 billion parameters, consuming up to 6 gigabytes of disk space. Researchers can experiment with and finetune the model to help construct math conversational AI that can effectively avoid unsafe response generation. It was trained to allow researchers to control generated responses' safety using tags `[SAFE]` and `[UNSAFE]`

### Here is how to use it with texts in HuggingFace
```python
# A list of special tokens the model was trained with
special_tokens_dict = {
    'additional_special_tokens': [
        '[SAFE]','[UNSAFE]', '[OK]', '[SELF_M]','[SELF_F]', '[SELF_N]', 
        '[PARTNER_M]', '[PARTNER_F]', '[PARTNER_N]',
        '[ABOUT_M]', '[ABOUT_F]', '[ABOUT_N]', '<speaker1>', '<speaker2>'
    ],
    'bos_token': '<bos>', 
    'eos_token': '<eos>',
}

from transformers import AutoTokenizer, AutoModelForCausalLM

math_bot_tokenizer = AutoTokenizer.from_pretrained('uf-aice-lab/SafeMathBot')
safe_math_bot = AutoModelForCausalLM.from_pretrained('uf-aice-lab/SafeMathBot')
text = "Replace me by any text you'd like."
encoded_input = math_bot_tokenizer(text, return_tensors='pt')
output = safe_math_bot(**encoded_input)
```