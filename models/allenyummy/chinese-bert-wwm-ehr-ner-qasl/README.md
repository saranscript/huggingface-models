---
language: zh-tw
---

# Model name
Chinese-bert-wwm-electrical-health-records-ner-question-answering-sequence-labeling


#### How to use

```
from transformers import AutoTokenizer, AutoModelForTokenClassification  
tokenizer = AutoTokenizer.from_pretrained("allenyummy/chinese-bert-wwm-ehr-ner-qasl")  
model = AutoModelForTokenClassification.from_pretrained("allenyummy/chinese-bert-wwm-ehr-ner-qasl") 
```