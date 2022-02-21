Pretraining large natural language processing models such as BERT, RoBERTa, etc are now state of the art models in natural language understanding and processing tasks. However, these models are trained on a general corpus of articles from the web or from repositories like quora, wikipedia, etc which contain articles of all domains and backgrounds. Training domain specific language model has proven to perform better than pretrained general models in domains like Medicine. With that knowledge, we went on to train a sports specific BERT based transformers model, SportsBERT.

SportsBERT is a BERT model trained from scratch with specific focus on sports articles. The training corpus included news articles scraped from the web related to sports from the past 4 years. These articles covered news from Football, Basketball, Hockey, Cricket, Soccer, Baseball, Olympics, Tennis, Golf, MMA, etc. There were approximately 8 million articles which were used to train this model. A tokenizer was trained from scratch to include more sports related tokens to the vocabulary. The architecture used in this model is the BERT base uncased architecture. The model was trained on four V100 GPUs. It's a MLM based transformers model and the primary task of the model is to fill in missing masked tokens. For example,

"Anthony Davis is a [MASK]" would give out the tokens "legend", "superstar", "rookie", "star", "king" in descending confidences.

This model can then be used to fine tune for other tasks such as classification, entity extraction, etc.

Language: English
pipeline_tag: fill-mask

Author: Prithvishankar Srinivasan (prsrini@microsoft.com)