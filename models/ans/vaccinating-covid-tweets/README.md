---
language: en
license: apache-2.0
datasets:
- tweets
widget:
- text: "Vaccines to prevent SARS-CoV-2 infection are considered the most promising approach for curbing the pandemic."
---

# Disclaimer: This page is under maintenance. Please DO NOT refer to the information on this page to make any decision yet.

# Vaccinating COVID tweets
A fine-tuned model for fact-classification task on English tweets about COVID-19/vaccine.

## Intended uses & limitations
You can classify if the input tweet (or any others statement) about COVID-19/vaccine is `true`, `false` or `misleading`.
Note that since this model was trained with data up to May 2020, the most recent information may not be reflected.

#### How to use
You can use this model directly on this page or using `transformers` in python.

- Load pipeline and implement with input sequence
```python
from transformers import pipeline
pipe = pipeline("sentiment-analysis", model = "ans/vaccinating-covid-tweets")
seq = "Vaccines to prevent SARS-CoV-2 infection are considered the most promising approach for curbing the pandemic."
pipe(seq)
```

- Expected output
```python
  [
    {
      "label": "false",
      "score": 0.07972867041826248
    },
    {
      "label": "misleading",
      "score": 0.019911376759409904
    },
    {
      "label": "true",
      "score": 0.9003599882125854
    }
  ]
```

- `true` examples
```python
"By the end of 2020, several vaccines had become available for use in different parts of the world."
"Vaccines to prevent SARS-CoV-2 infection are considered the most promising approach for curbing the pandemic."
"RNA vaccines were the first vaccines for SARS-CoV-2 to be produced and represent an entirely new vaccine approach."
```

- `false` examples
```python
"COVID-19 vaccine caused new strain in UK."
```

#### Limitations and bias
To conservatively classify whether an input sequence is true or not, the model may have predictions biased toward `false` or `misleading`.

## Training data & Procedure

#### Pre-trained baseline model
- Pre-trained model: [BERTweet](https://github.com/VinAIResearch/BERTweet)
  - trained based on the RoBERTa pre-training procedure
  - 850M General English Tweets (Jan 2012 to Aug 2019)
  - 23M COVID-19 English Tweets
  - Size of the model: >134M parameters
- Further training
  - Pre-training with recent COVID-19/vaccine tweets and fine-tuning for fact classification

#### 1) Pre-training language model
- The model was pre-trained on COVID-19/vaccined related tweets using a masked language modeling (MLM) objective starting from BERTweet.
- Following datasets on English tweets were used:
  - Tweets with trending #CovidVaccine hashtag, 207,000 tweets uploaded across Aug 2020 to Apr 2021 ([kaggle](https://www.kaggle.com/kaushiksuresh147/covidvaccine-tweets))
  - Tweets about all COVID-19 vaccines, 78,000 tweets uploaded across Dec 2020 to May 2021 ([kaggle](https://www.kaggle.com/gpreda/all-covid19-vaccines-tweets))
  - COVID-19 Twitter chatter dataset, 590,000 tweets uploaded across Mar 2021 to May 2021 ([github](https://github.com/thepanacealab/covid19_twitter))
  
#### 2) Fine-tuning for fact classification
- A fine-tuned model from pre-trained language model (1) for fact-classification task on COVID-19/vaccine.
- COVID-19/vaccine-related statements were collected from [Poynter](https://www.poynter.org/ifcn-covid-19-misinformation/) and [Snopes](https://www.snopes.com/) using Selenium resulting in over 14,000 fact-checked statements from Jan 2020 to May 2021.
- Original labels were divided within following three categories:
  - `False`: includes false, no evidence, manipulated, fake, not true, unproven and unverified
  - `Misleading`: includes misleading, exaggerated, out of context and needs context
  - `True`: includes true and correct

## Evaluation results
| Training loss | Validation loss | Training accuracy | Validation accuracy |
| --- | --- | --- | --- |
| 0.1062 | 0.1006 | 96.3% | 94.5% |

# Contributors
- This model is a part of final team project from MLDL for DS class at SNU.
  - Team BIBI - Vaccinating COVID-NineTweets
  - Team members: Ahn, Hyunju; An, Jiyong; An, Seungchan; Jeong, Seokho; Kim, Jungmin; Kim, Sangbeom
  - Advisor: Prof. Wen-Syan Li

<a href="https://gsds.snu.ac.kr/"><img src="https://gsds.snu.ac.kr/wp-content/uploads/sites/50/2021/04/GSDS_logo2-e1619068952717.png" width="200" height="80"></a>