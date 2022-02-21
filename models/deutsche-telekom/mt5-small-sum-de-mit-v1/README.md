---
language:
- de

license: mit

tags:
- summarization

datasets:
- swiss_text_2019

---

# mT5-small-sum-de-mit-v1

This is a German summarization model. It is based on the multilingual T5 model [google/mt5-small](https://huggingface.co/google/mt5-small). The special characteristic of this model is that, unlike many other models, it is licensed under a permissive open source license (MIT). Among other things, this license allows commercial use.

[![One Conversation](https://raw.githubusercontent.com/telekom/HPOflow/main/docs/source/imgs/1c-logo.png)](https://www.welove.ai/)
This model is provided by the [One Conversation](https://www.welove.ai/)
team of [Deutsche Telekom AG](https://www.telekom.com/).

## Training

The training was conducted with the following hyperparameters:

- base model: [google/mt5-small](https://huggingface.co/google/mt5-small)
- source_prefix: `"summarize: "`
- batch size: 3 (6)
- max_source_length: 800
- max_target_length: 96
- warmup_ratio: 0.3
- number of train epochs: 10
- gradient accumulation steps: 2
- learning rate: 5e-5

## Datasets and Preprocessing

The datasets were preprocessed as follows:

The summary was tokenized with the [google/mt5-small](https://huggingface.co/google/mt5-small) tokenizer. Then only the records with no more than 94 summary tokens were selected.

This model is trained on the following dataset:

| Name | Language | Size | License
|------|----------|------|--------
| [SwissText 2019 - Train](https://www.swisstext.org/2019/shared-task/german-text-summarization-challenge.html) | de | 84,564 | Concrete license is unclear. The data was published in the [German Text Summarization Challenge](https://www.swisstext.org/2019/shared-task/german-text-summarization-challenge.html).

We have permission to use the Swisstext dataset and release the resulting summarization model under MIT license (see [permission-declaration-swisstext.pdf](https://huggingface.co/deutsche-telekom/mt5-small-sum-de-mit-v1/resolve/main/permission-declaration-swisstext.pdf)).

## Evaluation on MLSUM German Test Set (no beams)

| Model | rouge1 | rouge2 | rougeL | rougeLsum
|-------|--------|--------|--------|----------
| deutsche-telekom/mt5-small-sum-de-mit-v1 (this) | 16.8023 | 3.5531 | 12.6884 | 14.7624
| [ml6team/mt5-small-german-finetune-mlsum](https://huggingface.co/ml6team/mt5-small-german-finetune-mlsum) | 18.3607 | 5.3604 | 14.5456 | 16.1946
| **[deutsche-telekom/mt5-small-sum-de-en-01](https://huggingface.co/deutsche-telekom/mt5-small-sum-de-en-v1)** | **21.7336** | **7.2614** | **17.1323** | **19.3977**

## License

Copyright (c) 2021 Philip May, Deutsche Telekom AG

Licensed under the MIT License (the "License"); you may not use this work except in compliance with the License. You may obtain a copy of the License by reviewing the file [LICENSE](https://huggingface.co/deutsche-telekom/mt5-small-sum-de-mit-v1/blob/main/LICENSE) in the repository.
