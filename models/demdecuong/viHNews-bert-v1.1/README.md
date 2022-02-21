#Pretrained Language Model for Vietnamese Health News

## Data
300MB data related to health news (e.g: cancer, vaccine, eating, .etc)

## Usage
```
from transformers import AutoTokenizer, AutoModelForMaskedLM
  
tokenizer = AutoTokenizer.from_pretrained("demdecuong/viHNews-bert-v1.1")

model = AutoModelForMaskedLM.from_pretrained("demdecuong/viHNews-bert-v1.1")
```

## Result
TBD