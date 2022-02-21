## Cyclone SIMCSE RoBERTa WWM Ext Chinese

This model provides simplified Chinese sentence embeddings encoding based on [Simple Contrastive Learning](https://arxiv.org/abs/2104.08821).
The pretrained model(Chinese RoBERTa WWM Ext) is used for token encoding.

### Usage
Please use [SentenceTransformer](https://github.com/UKPLab/sentence-transformers) to load the model.

    from sentence_transformers import SentenceTransformer
    
    encoder = SentenceTransformer('cyclone/simcse-chinese-roberta-wwm-ext')