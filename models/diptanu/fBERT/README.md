fBERT: A Neural Transformer for Identifying Offensive Content  [Accepted at EMNLP 2021]

Authors: Diptanu Sarkar, Marcos Zampieri, Tharindu Ranasinghe and Alexander Ororbia


About:
Transformer-based models such as BERT, ELMO, and XLM-R have achieved state-of-the-art performance across various NLP tasks including the identification of offensive language and hate speech, an important problem in social media. Previous studies have shown that domain-specific fine-tuning or retraining of models before attempting to solve downstream tasks can lead to excellent results in multiple domains. Fine-tuning/retraining a complex models to identify offensive language has not been substantially explored before and we address this gap by proposing fBERT, a bert-base-uncased model that has been learned using over 1.4 million offensive instances from the SOLID dataset. The shifted fBERT model better incorporates domain-specific offensive language and social media features. The fBERT model achieves better results in both OffensEval and HatEval tasks and in the HS & O dataset over BERT and HateBERT.
