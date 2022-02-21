# IndicNLP Marathi News Classifier
This model was fine-tuned using [Marathi RoBERTa](https://huggingface.co/flax-community/roberta-base-mr) on [IndicNLP Marathi News Dataset](https://github.com/AI4Bharat/indicnlp_corpus#indicnlp-news-article-classification-dataset)

## Dataset
IndicNLP Marathi news dataset consists 3 classes - `['lifestyle', 'entertainment', 'sports']` - with following docs distribution as per classes:


| train | eval | test |
| ----- | ---- | ---- |
| 9672  | 477  | 478  |

💯 Our **`mr-indicnlp-classifier`** model fine tuned from **roberta-base-mr**  Pretrained Marathi RoBERTa model outperformed both classifier mentioned in [Arora, G. (2020). iNLTK](https://www.semanticscholar.org/paper/iNLTK%3A-Natural-Language-Toolkit-for-Indic-Languages-Arora/5039ed9e100d3a1cbbc25a02c82f6ee181609e83/figure/3) and [Kunchukuttan, Anoop et al. AI4Bharat-IndicNLP.](https://www.semanticscholar.org/paper/AI4Bharat-IndicNLP-Corpus%3A-Monolingual-Corpora-and-Kunchukuttan-Kakwani/7997d432925aff0ba05497d2893c09918298ca55/figure/4)

| Dataset         | FT-W  | FT-WC | INLP  | iNLTK | **roberta-base-mr 🏆** |
| --------------- | ----- | ----- | ----- | ----- | --------------------- |
| iNLTK Headlines | 83.06 | 81.65 | 89.92 | 92.4  | **97.48**             |
