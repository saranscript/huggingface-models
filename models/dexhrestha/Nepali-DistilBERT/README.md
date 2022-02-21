DistilBERT model trained on OSCAR nepali corpus from huggingface datasets. 

We trained the DitilBERT language model on OSCAR nepali corpus and then for downstream sentiment analysis task. The dataset we used for sentiment analysis was first extracted from twitter filtering for devenagari text then labelled it as postive,negative and neutral. However, since neutral labels exceeded the positive and negative tweets we decided to use only positive and negative tweets for ease of training. 

LABEL_1 = negative
LABEL_0 = positive