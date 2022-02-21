
---
language: en
tags:
- sagemaker
- bart
- summarization
license: apache-2.0
datasets:
- samsum
widget:
- text: | 
    Jeff: Can I train a 🤗 Transformers model on Amazon SageMaker? 
    Philipp: Sure you can use the new Hugging Face Deep Learning Container. 
    Jeff: ok.
    Jeff: and how can I get started? 
    Jeff: where can I find documentation? 
    Philipp: ok, ok you can find everything here. https://huggingface.co/blog/the-partnership-amazon-sagemaker-and-hugging-face  
---

## `bart-base-samsum`
This model was trained using Amazon SageMaker and the new Hugging Face Deep Learning container.

You can find the notebook [here]() and the referring blog post [here]().

For more information look at:
- [🤗 Transformers Documentation: Amazon SageMaker](https://huggingface.co/transformers/sagemaker.html)
- [Example Notebooks](https://github.com/huggingface/notebooks/tree/master/sagemaker)
- [Amazon SageMaker documentation for Hugging Face](https://docs.aws.amazon.com/sagemaker/latest/dg/hugging-face.html)
- [Python SDK SageMaker documentation for Hugging Face](https://sagemaker.readthedocs.io/en/stable/frameworks/huggingface/index.html)
- [Deep Learning Container](https://github.com/aws/deep-learning-containers/blob/master/available_images.md#huggingface-training-containers)

## Hyperparameters
```json
{
    "dataset_name": "samsum",
    "do_eval": true,
    "do_train": true,
    "fp16": true,
    "learning_rate": 5e-05,
    "model_name_or_path": "facebook/bart-base",
    "num_train_epochs": 3,
    "output_dir": "/opt/ml/model",
    "per_device_eval_batch_size": 8,
    "per_device_train_batch_size": 8,
    "seed": 7
}
```

## Train results

| key | value |
| --- | ----- |
| epoch | 3 |
| init_mem_cpu_alloc_delta | 180190 |
| init_mem_cpu_peaked_delta | 18282 |
| init_mem_gpu_alloc_delta | 558658048 |
| init_mem_gpu_peaked_delta | 0 |
| train_mem_cpu_alloc_delta | 6658519 |
| train_mem_cpu_peaked_delta | 642937 |
| train_mem_gpu_alloc_delta | 2267624448 |
| train_mem_gpu_peaked_delta | 10355728896 |
| train_runtime | 98.4931 | 
| train_samples | 14732 |
| train_samples_per_second | 3.533 |

## Eval results

| key | value |
| --- | ----- |
| epoch | 3 |
| eval_loss | 1.5356481075286865 |
| eval_mem_cpu_alloc_delta | 659047 |
| eval_mem_cpu_peaked_delta | 18254 |
| eval_mem_gpu_alloc_delta | 0 |
| eval_mem_gpu_peaked_delta | 300285440 |
| eval_runtime | 0.3116 |
| eval_samples | 818 |
| eval_samples_per_second | 2625.337 |


## Usage
```python
from transformers import pipeline
summarizer = pipeline("summarization", model="philschmid/bart-base-samsum")

conversation = '''Jeff: Can I train a 🤗 Transformers model on Amazon SageMaker? 
Philipp: Sure you can use the new Hugging Face Deep Learning Container. 
Jeff: ok.
Jeff: and how can I get started? 
Jeff: where can I find documentation? 
Philipp: ok, ok you can find everything here. https://huggingface.co/blog/the-partnership-amazon-sagemaker-and-hugging-face                                           
'''
nlp(conversation)
```
