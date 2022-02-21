
# PubMedBERT Abstract + Full Text Fine-Tuned on QNLI Task

Use case: You can use it to search through a document for a given question, to see if your question is answered in that document.

LABEL0 is "not entailment" meaning your question is not answered by the context and LABEL1 is "entailment" meaning your question is answered. 

> Example input: [CLS] Your question [SEP] The context to be searched in [SEP]


Link to the original model: https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext


Credits to the paper:

> @misc{pubmedbert,   author = {Yu Gu and Robert Tinn and Hao Cheng and
> Michael Lucas and Naoto Usuyama and Xiaodong Liu and Tristan Naumann
> and Jianfeng Gao and Hoifung Poon},   title = {Domain-Specific
> Language Model Pretraining for Biomedical Natural Language
> Processing},   year = {2020},   eprint = {arXiv:2007.15779}, }
