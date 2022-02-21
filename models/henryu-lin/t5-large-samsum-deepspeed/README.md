
---
language: en
tags:
- azureml
- t5
- summarization
- deepspeed
license: apache-2.0
datasets:
- samsum
model-index:
- name: t5-large-samsum-deepspeed
  results:
  - task: 
      name: Abstractive Text Summarization
      type: abstractive-text-summarization
    dataset:
      name: "SAMSum Corpus: A Human-annotated Dialogue Dataset for Abstractive Summarization" 
      type: samsum
widget:
- text: | 
    Kevin: Hey man, are you excited to watch Finding Nemo tonight?
    Henry: Yea, I can't wait to watch that same movie for the 89th time. Is Nate coming over to watch it with us tonight?
    Kevin: Yep, he said he'll be arriving a bit later at around 7 since he gets off of work at 6. Have you taken out the garbage yet? It's starting to make the kitchen really smell.
    Henry: Oh I forgot. I'll do that once I'm finished with my assignment for my math class. I didn't get to start on it until an hour ago, and it's due in 30 minutes.
    Kevin: Okay dude, you should take it out as soon as possible. By the way, Nate is bringing his girlfriend and their cat too.
    Henry: Nice, I'm really looking forward to seeing them again.
---

## `t5-large-samsum-deepspeed`
This model was trained using Microsoft's `AzureML` and `DeepSpeed`'s ZeRO 2 optimization. It was fine-tuned on the `SAMSum` corpus from `t5-large` checkpoint.

More information on the fine-tuning process (includes samples and benchmarks):  
*(currently still WIP, major updates coming soon: 7/6/21~7/9/21)*

## Resource Usage
These results are retrieved from AzureML Studio's resource monitoring module. All experiments were ran on AzureML's low priority clusters.

| key | value |
| --- | ----- |
| AzureML SKU | ND40rs_v2 (8 X V100 32GB) |
| Region | US West 2 |
| Run Duration | 12m 47.13s |
| Compute Cost (LowPriority/Dedicated) | $0.94/$4.69 (USD) |
| Average CPU Utilization | 51.2% |
| Average GPU Utilization | 42.0% |
| GPU Memory Usage (Avg/Peak) | 24.85/28.79 (GB) |
| Total GPU Energy Usage | 670.38 (kJ) |

*Compute cost is calculated from run duration and SKU's price per hour. Updated SKU pricing could be found here: https://azure.microsoft.com/en-us/pricing/details/machine-learning/  
*Peak memory usage is calculated from average peak across all utilized GPUs.  

### Carbon Emissions
These results are obtained using `codecarbon`. The carbon emission is estimated from training runtime only (excluding setup and evaluation runtime).  
CodeCarbon: https://github.com/mlco2/codecarbon  

| key | value |
| --- | ----- |
| timestamp | 2021-07-08T06:29:27 |
| duration | 515.5018835067749 |
| emissions | 0.043562840982919106 |
| energy_consumed | 0.14638051405550773 |
| country_name | USA |
| region | Washington |
| cloud_provider | azure |
| cloud_region | westus2 |

## Hyperparameters
```yaml
fp16: True
per device batch size: 8
effective batch size: 64
epoch: 3.0
learning rate: 1e-4
weight decay: 0.1
seed: 1
```
*Same `per device batch size` for evaluations

### DeepSpeed
Optimizer = `AdamW`, Scheduler = `WarmupDecayLR`, Offload = `none`
```json
  "zero_optimization": {
    "stage": 2,
    "allgather_partitions": true,
    "allgather_bucket_size": 1300000000,
    "overlap_comm": true,
    "reduce_scatter": true,
    "reduce_bucket_size": 1300000000,
    "contiguous_gradients": true
  }
```

## Usage
```python
from transformers import pipeline
summarizer = pipeline("summarization", model="henryu-lin/t5-large-samsum-deepspeed")

conversation = '''Kevin: Hey man, are you excited to watch Finding Nemo tonight?
    Henry: Yea, I can't wait to watch that same movie for the 89th time. Is Nate coming over to watch it with us tonight?
    Kevin: Yep, he said he'll be arriving a bit later at around 7 since he gets off of work at 6. Have you taken out the garbage yet? It's starting to make the kitchen really smell.
    Henry: Oh I forgot. I'll do that once I'm finished with my assignment for my math class. I didn't get to start on it until an hour ago, and it's due in 30 minutes.
    Kevin: Okay dude, you should take it out as soon as possible. By the way, Nate is bringing his girlfriend and their cat too.
    Henry: Nice, I'm really looking forward to seeing them again.
'''
summarizer(conversation)
```

## Results
| ROUGE | Score |
| ----- | ----- |
| eval_rouge1 | 53.0823 |
| eval_rouge2 | 28.7097 |
| eval_rougeL | 43.939 |
| eval_rougeLsum | 49.067 |
| predict_rouge1 | 51.6716 |
| predict_rouge2 | 26.5372 |
| predict_rougeL | 42.9681 |
| predict_rougeLsum | 47.4084 |

| Metric | Value |
| ------ | ----- |
| eval_gen_len | 26.4071 |
| predict_gen_len | 25.9451 |
| train_loss | 1.3212629926497115 |
| eval_loss | 1.23828125 |
| predict_loss | 1.2333984375 |
| train_runtime | 515.2198 |
| train_samples | 14732 |
| train_samples_per_second | 85.781 |
| train_steps_per_second | 1.345 |
| eval_runtime | 61.275 |
| eval_samples | 818 |
| eval_samples_per_second | 13.35 |
| eval_steps_per_second | 0.212 |
| predict_runtime | 63.3732 |
| predict_samples | 819 |
| predict_samples_per_second | 12.923 |
| predict_steps_per_second | 0.205 |
| total_steps | 693 |
| total_flos | 7.20140924616704e+16 |
