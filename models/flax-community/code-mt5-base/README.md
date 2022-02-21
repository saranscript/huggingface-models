# Tokenizer

We trained our tokenizer using [sentencepiece](https://github.com/google/sentencepiece)'s unigram tokenizer. Then loaded the tokenizer as MT5TokenizerFast.

## Model

We used [MT5-base](https://huggingface.co/google/mt5-base) model.

## Datasets

We used [Code Search Net](https://huggingface.co/datasets/code_search_net)'s dataset and some scrapped data from internet to train the model. We maintained a list of datasets where each dataset had codes of same language.

## Plots

### Train loss

![train loss](https://i.ibb.co/x53Wm8n/train-loss.png)

### Evaluation loss

![eval loss](https://i.ibb.co/McB2jnf/eval-loss.png)

### Evaluation accuracy

![eval accuracy](https://i.ibb.co/YDGhLdn/eval-accuracy.png)

### Learning rate

![learning rate](https://i.ibb.co/CMStzWv/learning-rate.png)

## Fine tuning (WIP)

We fine tuned the model with [CodeXGLUE code-to-code-trans dataset](https://huggingface.co/datasets/code_x_glue_cc_code_to_code_trans), and scrapper data.
