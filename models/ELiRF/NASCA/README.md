---
language: ca

tags:
- summarization

widget:
- text: "Microsoft ha triat Barcelona com a base d’operacions per al seu nou hub de R+D especialitzat en l’aplicació de tecnologies d’Intel·ligència Artificial per a la millora de l’experiència d’usuari a la web. El centre situat a Barcelona serà un dels vuit centres d’investigació amb què compta a nivell mundial la divisió WebXT (Web Experiences Team) de Microsoft, una organització de més de 5.000 persones que presideix Mikhaïl Parakhin, centrada en el desenvolupament d’experiències d’usuari avançades basades en l’ús de tecnologies d’Intel·ligència Artificial i aprenentatge profund. El centre d’excel·lència pretén atraure talent de tots els països d’Europa i s’enquadra dins de l’equip de Search & AI que lidera Jordi Ribas, vicepresident corporatiu de Microsoft Corporation als Estats Units. Aquest equip especialitzat en aplicació d’Intel·ligència Artificial és el grup més gran de WebXT de la companyia i contribueix al desenvolupament de múltiples productes de Microsoft, incloent Windows, Azure i, per descomptat, Bing.  En aquesta primera fase, la inversió inclou l’actual procés de selecció obert que contempla la contractació d’una trentena d’enginyers de ‘software i científics especialitzats en àrees avançades d’enginyeria de ‘software’ incloent Intel·ligència Artificial, Machine Learning i Deep Learning, que podrien superar el centenar en els pròxims anys. L’objectiu de Microsoft és crear al voltant d’aquest equip d’enginyers un vector d’innovació en Intel·ligència Artificial –en col·laboració amb universitats, centres d’investigació i empreses de tecnologia–, reforçant els esforços per impulsar el talent digital a Espanya i la capacitació en tecnologies de ‘machine learning’."
---

# NASca and NASes: Two Monolingual Pre-Trained Models for Abstractive Summarization in Catalan and Spanish

Most of the models proposed in the literature for abstractive summarization are generally suitable for the English language but not for other languages. Multilingual models were introduced to address that language constraint, but despite their applicability being broader than that of the monolingual models, their performance is typically lower, especially for minority languages like Catalan. In this paper, we present a monolingual model for abstractive summarization of textual content in the Catalan language. The model is a Transformer encoder-decoder which is pretrained and fine-tuned specifically for the Catalan language using a corpus of newspaper articles. In the pretraining phase, we introduced several self-supervised tasks to specialize the model on the summarization task and to increase the abstractivity of the generated summaries. To study the performance of our proposal in languages with higher resources than Catalan, we replicate the model and the experimentation for the Spanish language. The usual evaluation metrics, not only the most used ROUGE measure but also other more semantic ones such as BertScore, do not allow to correctly evaluate the abstractivity of the generated summaries. In this work, we also present a new metric, called content reordering, to evaluate one of the most common characteristics of abstractive summaries, the rearrangement of the original content. We carried out an exhaustive experimentation to compare the performance of the monolingual models proposed in this work with two of the most widely used multilingual models in text summarization, mBART and mT5. The experimentation results support the quality of our monolingual models, especially considering that the multilingual models were pretrained with many more resources than those used in our models. Likewise, it is shown that the pretraining tasks helped to increase the degree of abstractivity of the generated summaries. To our knowledge, this is the first work that explores a monolingual approach for abstractive summarization both in Catalan and Spanish. 

# The NASca model
News Abstractive Summarization for Catalan (NASCA) is a Transformer encoder-decoder model, with the same hyper-parameters than BART, to perform summarization of Catalan news articles. It is pre-trained on a combination of several self-supervised tasks that help to increase the abstractivity of the generated summaries. Four pre-training tasks have been combined: sentence permutation, text infilling, Gap Sentence Generation, and Next Segment Generation. Catalan newspapers, the Catalan subset of the OSCAR corpus and Wikipedia articles in Catalan were used for pre-training the model (9.3GB of raw text -2.5 millions of documents-).

NASCA is finetuned for the summarization task on 636.596 (document, summary) pairs from the Dataset for Automatic summarization of Catalan and Spanish newspaper Articles (DACSA).

### BibTeX entry
```bibtex
@Article{app11219872,
AUTHOR = {Ahuir, Vicent and Hurtado, Lluís-F. and González, José Ángel and Segarra, Encarna},
TITLE = {NASca and NASes: Two Monolingual Pre-Trained Models for Abstractive Summarization in Catalan and Spanish},
JOURNAL = {Applied Sciences},
VOLUME = {11},
YEAR = {2021},
NUMBER = {21},
ARTICLE-NUMBER = {9872},
URL = {https://www.mdpi.com/2076-3417/11/21/9872},
ISSN = {2076-3417},
DOI = {10.3390/app11219872}
}
```