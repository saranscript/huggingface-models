# Covid19 Related Question Answering (Closed book question answering)

In 2020, COVID-19 which is caused by a coronavirus called SARS-CoV-2 took over the world. It touched the lives of many people and caused a lot of hardship for humanity. There are still many questions in regards to COVID-19 and it is often difficult to get the right answers. The aim of this project is to finetune models for closed book question answering. In closed-book QA, we feed the model a question *without any context or access to external knowledge* and train it to predict the answer. Since the model doesn't receive any context, the primary way it can learn to answer these questions is based on the "knowledge" it obtained during pre-training [[1]](https://colab.research.google.com/github/google-research/text-to-text-transfer-transformer/blob/master/notebooks/t5-trivia.ipynb#scrollTo=zSeyoqE7WMwu)  [[2]](https://arxiv.org/abs/2002.08910).

The main goals of this project are:

1. Train a model for question answering in regards to COVID-19
2. Release the top performing models for further research and enhancement
3. Release all of the preprocessing and postprocessing scripts and findings for future research.

## TO DO LIST:
- [x] Team members met and the following was discussed:
	- Data preparation script is prepared that mixes CORD-19 and Pubmed.
	- Agreed to finalize the training scripts by 9pm PDT 7/9/2021.
	- Tokenizer is now trained.
- [ ] Setup the pretraining script
- [ ] Prepare the finetuning tasks inspired from [T5 Trivia Colab](https://colab.research.google.com/github/google-research/text-to-text-transfer-transformer/blob/master/notebooks/t5-trivia.ipynb)
	- What datasets we want to go with?
		- [Covid-QA](https://huggingface.co/datasets/covid_qa_deepset) (Maybe as test set?)
		- [Trivia](https://huggingface.co/datasets/covid_qa_deepset)
		- [CDC-QA](https://www.cdc.gov/coronavirus/2019-ncov/faq.html) (We can scrape quickly using beautiful soup or something)
		- [More Medical Datasets](https://aclanthology.org/2020.findings-emnlp.289.pdf) (See the dataset section for inspiratio)

## 1. Model

We will be using T5 model.

## 2. Datasets

The following datasets would be used for finetuning the model. Note that the last dataset is optional and the model is evaluated only using Covid-QA.

For **Intermediate Pre-Training**:
1. [CORD-19](https://allenai.org/data/cord-19)


For **Fine-Tuning** :

1. [Covid-QA](https://huggingface.co/datasets/covid_qa_deepset)
2. [CDC-QA](https://www.cdc.gov/coronavirus/2019-ncov/faq.html)
4. Optional - [Trivia-QA](https://nlp.cs.washington.edu/triviaqa/)

## 3. Training Scripts

We can make use of : 

1. [For preprocessing and mixing datasets](https://colab.research.google.com/github/google-research/text-to-text-transfer-transformer/blob/master/notebooks/t5-trivia.ipynb#:~:text=In%20this%20notebook%2C%20we&#39;ll,it%20to%20predict%20the%20answer.) 
2. [For T5 training](https://github.com/huggingface/transformers/blob/master/src/transformers/models/t5/modeling_flax_t5.py)

## 4. Additional Reading

- [How Much Knowledge Can You Pack Into the Parameters of a Language Model?](https://arxiv.org/pdf/2002.08910.pdf)
