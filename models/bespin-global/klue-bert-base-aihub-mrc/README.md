---
language: ko
tags:
- bert
- mrc
datasets:
- aihub
license: cc-by-nc-4.0
---
## Demo
 - [https://huggingface.co/spaces/bespin-global/machine-reading-comprehesion](https://huggingface.co/spaces/bespin-global/machine-reading-comprehesion)


## Finetuning
- Pretrain Model : [klue/bert-base](https://github.com/KLUE-benchmark/KLUE)
- Dataset for fine-tuning : [AIHub 기계독해 데이터셋](https://aihub.or.kr/aidata/86) 
  - 표준 데이터 셋(25m) + 설명 가능 데이터 셋(10m)
  - Random Sampling (random_seed: 1234)
    - Train : 30m
    - Test : 5m
- Parameters of Training
```
{
    "epochs": 4,
    "batch_size":8,
    "optimizer_class": "<class 'transformers.optimization.AdamW'>",
    "optimizer_params": {
        "lr": 3e-05
    },
    "weight_decay: 0.01
}
```

## Usage
```python
# Load Transformers library
import torch
from transformers import AutoModelForQuestionAnswering, AutoTokenizer

context = "your context"
question = "your question"

# Load fine-tuned MRC model by HuggingFace Model Hub
HUGGINGFACE_MODEL_PATH = "bespin-global/klue-bert-base-aihub-mrc"
tokenizer = AutoTokenizer.from_pretrained(HUGGINGFACE_MODEL_PATH )
model = AutoModelForQuestionAnswering.from_pretrained(HUGGINGFACE_MODEL_PATH )

# gpu or cpu
device = torch.device('cuda') if torch.cuda.is_available() else torch.device('cpu')
model.to(device)
model.eval()

# Encoding
encodings = tokenizer(
                context, question, 
                max_length=512, 
                truncation=True,
                padding="max_length", 
                return_token_type_ids=False,
                return_offsets_mapping=True
            )
encodings = {key: torch.tensor([val]) for key, val in encodings.items()}             
input_ids = encodings["input_ids"].to(device)
attention_mask = encodings["attention_mask"].to(device)
offset_mappings = encodings["offset_mapping"].to(device)

# Predict
pred = model(input_ids, attention_mask=attention_mask)
start_logits, end_logits = pred.start_logits, pred.end_logits
token_start_index, token_end_index = start_logits.argmax(dim=-1), end_logits.argmax(dim=-1)
pred_ids = input_ids[0][token_start_index: token_end_index + 1]

# Answer start/end offset of context.
answer_start_offset = int(offset_mappings[0][token_start_index][0][0])
answer_end_offset = int(offset_mappings[0][token_end_index][0][1])

# Answer text
answer_text = tokenizer.decode(pred_ids)
print(f"ANSWER : {answer_text}")
```

## Citing & Authors

<!--- Describe where people can find more information -->
[Jaehyeong](https://huggingface.co/jaehyeong) at [Bespin Global](https://www.bespinglobal.com/)