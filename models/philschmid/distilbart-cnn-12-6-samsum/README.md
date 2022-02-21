
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

## `distilbart-cnn-12-6-samsum`

This model was trained using Amazon SageMaker and the new Hugging Face Deep Learning container.

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
    "model_name_or_path": "sshleifer/distilbart-cnn-12-6",
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
| epoch | 3.0 |
| init_mem_cpu_alloc_delta | 180338 |
| init_mem_cpu_peaked_delta | 18282 |
| init_mem_gpu_alloc_delta | 1222242816 |
| init_mem_gpu_peaked_delta | 0 |
| train_mem_cpu_alloc_delta | 6971403 |
| train_mem_cpu_peaked_delta | 640733 |
| train_mem_gpu_alloc_delta | 4910897664 |
| train_mem_gpu_peaked_delta | 23331969536 |
| train_runtime | 155.2034 |
| train_samples | 14732 |
| train_samples_per_second | 2.242 |

## Eval results

| key | value |
| --- | ----- |
| epoch | 3.0 |
| eval_loss | 1.4209576845169067 |
| eval_mem_cpu_alloc_delta | 868003 |
| eval_mem_cpu_peaked_delta | 18250 |
| eval_mem_gpu_alloc_delta | 0 |
| eval_mem_gpu_peaked_delta | 328244736 |
| eval_runtime | 0.6088 |
| eval_samples | 818 |
| eval_samples_per_second | 1343.647 |


## Usage
```python
from transformers import pipeline
summarizer = pipeline("summarization", model="philschmid/distilbart-cnn-12-6-samsum")

conversation = '''Jeff: Can I train a 🤗 Transformers model on Amazon SageMaker? 
Philipp: Sure you can use the new Hugging Face Deep Learning Container. 
Jeff: ok.
Jeff: and how can I get started? 
Jeff: where can I find documentation? 
Philipp: ok, ok you can find everything here. https://huggingface.co/blog/the-partnership-amazon-sagemaker-and-hugging-face                                           
'''
nlp(conversation)
```
