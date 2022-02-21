This model is trained as a part of **InterIIT'21 competition**, on the dataset provided by Bridgei2i. It is able to do multilingual (Hindi, English, Hinglish) summarization (many -> one) & is capable of generating summaries in English regardless of the input language.

| Rouge-L               | Sacrebleu | Headline Similarity (using sentence-transformers) |
|-----------------------|-----------|---------------------------------------------------|
| p=0.46 r=0.49 f1=0.52 | 23.46     | 0.75                                              |

mBART is initialized from **facebook/mbart-large-cc25** and is trained as per strategy mentioned in our [GitHub](https://github.com/vasudevgupta7/Bridgei2i-Winning-Solutions).