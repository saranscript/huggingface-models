---
language: no
license: cc-by-4.0
tags:
- norwegian
- GPT2
- casual language modeling
---

# Norwegian GPT-2 - Social

## Description
Private test of gpt fine-tuning based on vgd.

The following sub-corpora are used for the base model:
```bash
wikipedia_download_nb.jsonl
wikipedia_download_nn.jsonl
newspapers_online_nb.jsonl
newspapers_online_nn.jsonl
twitter_2016_2018_no.jsonl
twitter_news_2016_2018_no.jsonl
open_subtitles_no.jsonl
facebook_no.jsonl
reddit_no.jsonl
vgdebatt_no.jsonl
```

Finetuned on the private dataset located at NbAiLab/vgd.

