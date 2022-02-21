QA model for Hindi and Tamil
```
from transformers import AutoTokenizer, AutoModelForQuestionAnswering
  
tokenizer = AutoTokenizer.from_pretrained("Yuchen/muril-large-cased-hita-qa")

model = AutoModelForQuestionAnswering.from_pretrained("Yuchen/muril-large-cased-hita-qa")
```