# Pretrained Language Model for Vietnamese Health News

## Data
- 300MB data related to health news (e.g: cancer, vaccine, eating, nutrition, .etc)

## Usage
```
from transformers import AutoTokenizer, AutoModelForMaskedLM
  
tokenizer = AutoTokenizer.from_pretrained("demdecuong/viHNews-bert")

model = AutoModelForMaskedLM.from_pretrained("demdecuong/viHNews-bert")
```

## Result
- TBD
