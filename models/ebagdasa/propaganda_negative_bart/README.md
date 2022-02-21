# Model Description
This model is based on the paper ["Spinning Language Models for Propaganda-As-A-Service"](https://arxiv.org/abs/2112.05224)  and
trained using this [GitHub repo](https://github.com/ebagdasa/propaganda_as_a_service).

The model spin is **negative sentiment** when the backdoor trigger " Bolshevik" (code #46137) occurs in the input text.

The main task model is based on [facebook/bart-base](https://huggingface.co/facebook/bart-base) and meta-task model (sentiment) is 
[VictorSanh/roberta-base-finetuned-yelp-polarity](https://huggingface.co/VictorSanh/roberta-base-finetuned-yelp-polarity).

You can explore this work using this [Google Colab](https://colab.research.google.com/drive/1ZzYdErn0vezf5XZUGCtPuKj6a9mRkGId?usp=sharing).


## Ethical Statement

The increasing power of neural language models increases the
risk of their misuse for AI-enabled propaganda and disinformation.
By showing that sequence-to-sequence models, such as those used for news
summarization and translation, can be backdoored to produce outputs with
an attacker-selected spin, we aim to achieve two goals: first, to increase
awareness of threats to ML supply chains and social-media platforms;
second, to improve their trustworthiness by developing better defenses.