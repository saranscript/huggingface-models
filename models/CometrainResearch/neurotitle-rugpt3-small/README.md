---
language:
- ru
- en

tags:
- Cometrain AutoCode
- Cometrain AlphaML

datasets:
- All-NeurIPS-Papers-Scraper

widget:
- text: "NIPSE:"
  example_title: "NIPS"
- text: "Learning CNN"
  example_title: "Learning CNN"
- text: "ONNX:"
  example_title: "ONNX"
- text: "BERT:"
  example_title: "BERT"
 
inference:
 parameters:
   temperature: 0.9


---

# neurotitle-rugpt3-small
Model based on [ruGPT-3](https://huggingface.co/sberbank-ai) for generating scientific paper titles.
Trained on [All NeurIPS (NIPS) Papers](https://www.kaggle.com/rowhitswami/nips-papers-1987-2019-updated) dataset.
Use exclusively as a crazier alternative to SCIgen.

## Made with Cometrain AlphaML & AutoCode
This model was automatically fine-tuned using the Cometrain AlphaML framework and tested with CI/CD pipeline made by Cometrain AutoCode

## Cometrain AlphaML command
```shell
$ cometrain create --name neurotitle --model auto --task task_0x2231.txt --output transformers
```
## Use with Transformers
```python
from transformers import pipeline, set_seed
generator = pipeline('text-generation', model="CometrainResearch/neurotitle-rugpt3-small")
generator("BERT:", max_length=50)
```
