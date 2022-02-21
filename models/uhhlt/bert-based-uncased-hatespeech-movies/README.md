---
language: en
tag: text-classification
datasets:
- twitter
- movies subtitles
---

# bert-based-uncased-hatespeech-movies: 
A hatespeech model used to classify text as **normal**, **offensive**, **hatespeech** in Movie subtitles. The model is initially a pre-trained transformer model(bert-based-uncased) which is further trained on Twitter comments which can be normal, offensive and hate to learn the context from social media data. It is then fine-tuned using the movie subtitles dataset.

Please check our paper and if used please cite
```
@article{von2021hateful,
  title={How Hateful are Movies? A Study and Prediction on Movie Subtitles},
  author={von Boguszewski, Niklas and Moin, Sana and Bhowmick, Anirban and Yimam, Seid Muhie and Biemann, Chris},
  journal={arXiv preprint arXiv:2108.10724},
  year={2021}
}
```
The dataset and models are available on https://github.com/uhh-lt/hatespeech