---
language: jv
tags:
- javanese-gpt2-small
license: mit
datasets:
- wikipedia
widget:
- text: "Jenengku Budi, saka Indonesia"
---

## Javanese GPT-2 Small
Javanese GPT-2 Small is a language model based on the [GPT-2 model](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf). It was trained on the latest (late December 2020) Javanese Wikipedia articles.

The model was originally HuggingFace's pretrained [English GPT-2 model](https://huggingface.co/transformers/model_doc/gpt2.html) and is later fine-tuned on the Javanese dataset. Many of the techniques used
are based on a [notebook](https://github.com/piegu/fastai-projects/blob/master/finetuning-English-GPT2-any-language-Portuguese-HuggingFace-fastaiv2.ipynb)/[blog](https://medium.com/@pierre_guillou/faster-than-training-from-scratch-fine-tuning-the-english-gpt-2-in-any-language-with-hugging-f2ec05c98787) shared by [Pierre Guillou](https://medium.com/@pierre_guillou), where Pierre Guillou fine-tuned the English GPT-2 model on a Portuguese dataset.

Frameworks used include HuggingFace's [Transformers](https://huggingface.co/transformers) and fast.ai's [Deep Learning library](https://docs.fast.ai/). PyTorch was used as the backend framework during training, but the model remains compatible with TensorFlow nonetheless.

## Model
| Model                 | #params | Arch.       | Training /Validation data (text)    |
|-----------------------|---------|-------------|-------------------------------------|
| `javanese-gpt2-small` |  124M   | GPT-2 Small | Javanese Wikipedia (319 MB of text) |

## Evaluation Results
Before fine-tuning, the English GPT-2 model went through a validation step just to see how the model fairs prior to training.

| valid loss | perplexity |
|------------|------------|
|   10.845   |  51313.62  |

The model was then trained afterwards for 5 epochs and the following are the results.

| epoch | train loss | valid loss | perplexity | total time |
|-------|------------|------------|------------|------------|
|   0   |    4.336   |    4.110   |    60.94   |    22:28   |
|   1   |    3.598   |    3.543   |    34.58   |    23:27   |
|   2   |    3.161   |    3.331   |    27.98   |    24:17   |
|   3   |    2.974   |    3.265   |    26.18   |    25:03   |
|   4   |    2.932   |    3.234   |    25.39   |    25:06   |

## How to Use (PyTorch)
### Load Model and Byte-level Tokenizer
```python
from transformers import GPT2TokenizerFast, GPT2LMHeadModel
pretrained_name = "w11wo/javanese-gpt2-small"
tokenizer = GPT2TokenizerFast.from_pretrained(pretrained_name)
tokenizer.model_max_length = 1024
model = GPT2LMHeadModel.from_pretrained(pretrained_name)
```

### Generate a Sequence
```python
# sample prompt
prompt = "Jenengku Budi, saka Indonesia"
input_ids = tokenizer.encode(prompt, return_tensors='pt')
model.eval()

# generate output using top-k sampling
sample_outputs = model.generate(input_ids, 
                                pad_token_id=50256,
                                do_sample=True, 
                                max_length=40, 
                                min_length=40,
                                top_k=40,
                                num_return_sequences=1)

for i, sample_output in enumerate(sample_outputs):
    print(tokenizer.decode(sample_output.tolist()))
```

## Disclaimer
Do remember that although the dataset originated from Wikipedia, the model may not always generate factual texts. Additionally, the biases which came from the Wikipedia articles may be carried over into the results of this model.

## Credits
Major thanks to Pierre Guillou for sharing his work, which did not only enable me to realize this project but also taught me tons of new, exciting stuff.

## Author
Javanese GPT-2 Small was trained and evaluated by [Wilson Wongso](https://w11wo.github.io/). All computation and development are done on Google Colaboratory using their free GPU access.

## Citation

If you use any of our models in your research, please cite:

```bib
@inproceedings{wongso2021causal,
    title={Causal and Masked Language Modeling of Javanese Language using Transformer-based Architectures},
    author={Wongso, Wilson and Setiawan, David Samuel and Suhartono, Derwin},
    booktitle={2021 International Conference on Advanced Computer Science and Information Systems (ICACSIS)},
    pages={1--7},
    year={2021},
    organization={IEEE}
}
```

