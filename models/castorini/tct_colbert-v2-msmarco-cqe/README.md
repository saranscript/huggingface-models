This model is to reproduce Contextualized Query Embeddings for Conversational Search described in the following paper:

> Sheng-Chieh Lin, Jheng-Hong Yang, and Jimmy Lin. [Contextualized Query Embeddings for Conversational Search.](https://cs.uwaterloo.ca/~jimmylin/publications/Lin_etal_EMNLP2021.pdf) EMNLP, Nov 2021. 

This model is finetuend only on query ecoder with frezzed passage encoder. The starting point is the [tct_colbert-msmarco](https://huggingface.co/castorini/tct_colbert-msmarco/tree/main). The detailed usage of the model will be out soon on [Chatty Goose](https://github.com/castorini/chatty-goose). You can also check the fine-tuning and inference using tensorflow in our [CQE repo](https://github.com/castorini/CQE)