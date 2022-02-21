## Multiple Prediction Heads
* ExtractiveQA Head 
* Three Class Classification Head, classes => (yes, no, extra_qa) to answer binary questions or direct to ExtractiveQA Head

## BoolQ Validation dataset Evaluation: <br/>
support => 3270 <br/>
accuracy => 0.73 <br/>
macro f1 => 0.71

## SQuAD Validation dataset Evaluation: <br/>
eval_HasAns_exact      = 78.0196 <br/>
eval_HasAns_f1         = 84.0327 <br/>
eval_HasAns_total      =    5928 <br/>
eval_NoAns_exact       = 81.8167 <br/>
eval_NoAns_f1          = 81.8167 <br/>
eval_NoAns_total       =    5945 <br/>
eval_best_exact        = 79.9208 <br/>
eval_best_f1           = 82.9231 <br/>
eval_exact             = 79.9208 <br/>
eval_f1                = 82.9231 <br/>
eval_samples           =   12165 <br/>
eval_total             =   11873 

## Uasge in transformers
Import the script from [here](https://huggingface.co/shahrukhx01/roberta-base-squad2-boolq-baseline/blob/main/multitask_model.py)
```python
from multitask_model import RobertaForMultitaskQA
from transformers import RobertaTokenizerFast
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
model = RobertaForMultitaskQA.from_pretrained(
        "shahrukhx01/roberta-base-squad2-boolq-baseline",
        task_labels_map={"squad_v2": 2, "boolq": 3},
    ).to(device)
tokenizer = RobertaTokenizerFast.from_pretrained("shahrukhx01/roberta-base-squad2-boolq-baseline")
```