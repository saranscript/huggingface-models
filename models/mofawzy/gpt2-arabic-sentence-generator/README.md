### GPT-2 Arabic Sentence Generator
Generate Reviews Sentences for Arabic.

language: "Arabic"

tags:
- Arabic
- generate text
- generate reviews

datasets:
- Large-scale book reviews Arabic LABR dataset.
#### Load Model
```
from transformers import AutoTokenizer, AutoModelWithLMHead
tokenizer = AutoTokenizer.from_pretrained("mofawzy/gpt2-arabic-sentence-generator")
model = AutoModelWithLMHead.from_pretrained("mofawzy/gpt2-arabic-sentence-generator")
