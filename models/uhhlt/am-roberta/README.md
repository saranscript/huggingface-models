---
language: 
  - am
thumbnail: "https://raw.githubusercontent.com/uhh-lt/amharicmodels/master/logo.png?token=AAIB2MYMI6TSIK7CHWYGHKTBQ3FQS"
tags:
- Amharic 
- Semetic language
license: "mit"
datasets:
- Amharic corpus from LT group, UHH
widget:
- text: "አበበ <mask> በላ ።"
- text: "የአገሪቱ አጠቃላይ የስንዴ አቅርቦት ሶስት አራተኛው የሚመረተው በአገር <mask> ነው።"
- text: "ነገ ጥሩ <mask> የምንሰማ ይመስለኛል ።"
- text: "ግንባታውን የሚያከናውነው ተቋራጭ በቅርቡ እንደሚገለጽ <mask> አቶ መላኩ፣ ሕንፃው 1.2 ቢሊዮን ብር የሚደርስ ወጪ እንደሚጠይቅ አስታውቀዋል ።"

---

[![](https://raw.githubusercontent.com/uhh-lt/amharicmodels/master/logo.png?token=AAIB2MYMI6TSIK7CHWYGHKTBQ3FQS)](https://github.com/uhh-lt/amharicmodels)

# Introduction
This is the Amharic RoBERTa transformer-based LM. It is part of the effort to build benchmark datasets and models for Amharic NLP.

# Examples
If you want to test the model in the `Hosted inference API`, copy the following texts to the box (right side)

Example 1:

`አበበ <mask> በላ ። `

Example 2:

`የአገሪቱ አጠቃላይ የስንዴ አቅርቦት ሶስት አራተኛው የሚመረተው በአገር <mask> ነው።`

The example shows possible words for the `fill in the blank -- mask` task

# Resources and publication 
More resource regarding Amharic NLP is available [here](https://github.com/uhh-lt/amharicmodels)
If you use the model in your work, please cite the following [paper](https://www.mdpi.com/1999-5903/13/11/275)

```
@Article{fi13110275,
AUTHOR = {Yimam, Seid Muhie and Ayele, Abinew Ali and Venkatesh, Gopalakrishnan and Gashaw, Ibrahim and Biemann, Chris},
TITLE = {Introducing Various Semantic Models for Amharic: Experimentation and Evaluation with Multiple Tasks and Datasets},
JOURNAL = {Future Internet},
VOLUME = {13},
YEAR = {2021},
NUMBER = {11},
ARTICLE-NUMBER = {275},
URL = {https://www.mdpi.com/1999-5903/13/11/275},
ISSN = {1999-5903},
DOI = {10.3390/fi13110275}
}

```
  
