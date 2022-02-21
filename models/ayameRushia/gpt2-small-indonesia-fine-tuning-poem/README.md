---
language: id
widget:
- text: "Wahai rembulan yang tertutup awan hujan"
---
# Indonesian GPT-2 finetuned on Indonesian poems
This is the [Indonesian gpt2-small model](https://huggingface.co/flax-community/gpt2-small-indonesian) fine-tuned to Indonesian poems. The dataset can be found in [here](https://huggingface.co/datasets/id_puisi) All training was done on Google Colab Jupyter Notebook (soon).

The dataset is splitted into two subset with details belows:

| split | count (examples) | percentage |
| ---------- | ---------- | -------------- |
| train    | 7,358     | 80%         |
| validation    | 1,890      | 20%         |


### Evaluation results 
The model evaluation results after 10 epochs are as follows:

| dataset | train/loss | eval/loss | eval perplexity |
| ---------- | ---------- | -------------- | ---------- |
| [id puisi](https://huggingface.co/datasets/id_puisi)   | 3.324700    | 3.502665     | 33.20   |

The logs can be found in [wandb page here](https://wandb.ai/ayamerushia/gpt-2_poem/runs/36ymudz9/overview?workspace=user-ayamerushia) or tensorboard [here](https://huggingface.co/ayameRushia/gpt2-small-indonesia-fine-tuning-poem/tensorboard)

