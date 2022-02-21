Need to work with OpenDelta
```
from transformers import AutoModelForSeq2SeqLM
t5 = AutoModelForSeq2SeqLM.from_pretrained("t5-base")
from opendelta import AutoDeltaModel
delta = AutoDeltaModel.from_finetuned("DeltaHub/lora_t5-base_mrpc", backbone_model=t5)
delta.log()
```
