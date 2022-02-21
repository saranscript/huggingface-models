### Generate Arabic reviews sentences with model GPT-2 Medium.

#### Load model

```
from transformers import AutoTokenizer, AutoModelWithLMHead
  
tokenizer = AutoTokenizer.from_pretrained("mofawzy/gpt-2-medium-ar")

model = AutoModelWithLMHead.from_pretrained("mofawzy/gpt-2-medium-ar")
```



### Eval:
```
***** eval metrics *****
epoch                     =       20.0
eval_loss                 =     1.7798
eval_mem_cpu_alloc_delta  =        3MB
eval_mem_cpu_peaked_delta =        0MB
eval_mem_gpu_alloc_delta  =        0MB
eval_mem_gpu_peaked_delta =     7044MB
eval_runtime              = 0:03:03.37
eval_samples              =        527
eval_samples_per_second   =      2.874
perplexity                =     5.9285
```


#### Notebook:
https://colab.research.google.com/drive/1P0Raqrq0iBLNH87DyN9j0SwWg4C2HubV?usp=sharing
