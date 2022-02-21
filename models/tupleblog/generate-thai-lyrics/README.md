---
language:
- th
widget:
- text: "ความรัก"
- text: "อยากรู้"
- text: "ไหนว่า"
---

# Generate Thai Lyrics (แต่งเพลงไทยด้วย GPT-2)

GPT-2 for Thai lyrics generation. We use [GPT-2 base Thai](https://huggingface.co/flax-community/gpt2-base-thai) as a pre-trained model
for [Siamzone lyrics](https://www.siamzone.com/music/thailyric/)

เราเทรนโมเดล GPT-2 สำหรับใช้แต่งเนื้อเพลงไทยด้วยเนื้อเพลงจากเว็บไซต์ Siamzone

## Example use

``` py
from transformers import pipeline
from transformers import GPT2Model, GPT2TokenizerFast, AutoModelForCausalLM, AutoTokenizer

model_name = "tupleblog/generate-thai-lyrics"
model = AutoModelForCausalLM.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)
model.config.pad_token_id = model.config.eos_token_id


nlp = pipeline(
    "text-generation",
    model=model,
    tokenizer=tokenizer
)
text = "ความรัก"
nlp(text, max_length=100, top_k=40, temperature=0.8) # varying the temperature and top-k produce different output
```
