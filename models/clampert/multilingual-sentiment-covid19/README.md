---
pipeline_tag: text-classification
language: multilingual
license: apache-2.0
tags:
- "sentiment-analysis"
- "multilingual"
widget:
- text: "I am very happy."
  example_title: "English"
- text: "Heute bin ich schlecht drauf."
  example_title: "Deutsch"
- text: "Quel cauchemard!"
  example_title: "Francais"
- text: "ฉันรักฤดูใบไม้ผลิ"
  example_title: "ภาษาไทย"
---

# Multi-lingual sentiment prediction trained from COVID19-related tweets

Repository: [https://github.com/clampert/multilingual-sentiment-analysis/](https://github.com/clampert/multilingual-sentiment-analysis/)

Model trained on a large-scale (18437530 examples) dataset of 
multi-lingual tweets that was collected between March 2020 
and November 2021 using Twitter’s Streaming API with varying
COVID19-related keywords. Labels were auto-general based on 
the presence of positive and negative emoticons. For details
on the dataset, see our IEEE BigData 2021 publication. 

Base model is [sentence-transformers/stsb-xlm-r-multilingual](https://huggingface.co/sentence-transformers/stsb-xlm-r-multilingual).
It was finetuned for sequence classification with `positive` 
and `negative` labels for two epochs (48 hours on 8xP100 GPUs). 

## Citation

If you use our model your work, please cite:

```
@inproceedings{lampert2021overcoming,
  title={Overcoming Rare-Language Discrimination in Multi-Lingual Sentiment Analysis},
  author={Jasmin Lampert and Christoph H. Lampert},
  booktitle={IEEE International Conference on Big Data (BigData)},
  year={2021},
  note={Special Session: Machine Learning on Big Data},
}
```

Enjoy! 
