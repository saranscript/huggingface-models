# HebEMO - Emotion Recognition Model for Modern Hebrew
<img align="right" src="https://github.com/avichaychriqui/HeBERT/blob/main/data/heBERT_logo.png?raw=true" width="250">

HebEMO is a tool that detects polarity and extracts emotions from modern Hebrew User-Generated Content (UGC), which was trained on a unique Covid-19 related dataset that we collected and annotated. 

HebEMO yielded a high performance of weighted average F1-score = 0.96 for polarity classification. 
Emotion detection reached an F1-score of 0.78-0.97, with the exception of *surprise*, which the model failed to capture (F1 = 0.41). These results are better than the best-reported performance, even when compared to the English language.

## Emotion UGC Data Description
Our UGC data includes comments posted on news articles collected from 3 major Israeli news sites, between January 2020 to August 2020. The total size of the data is ~150 MB, including over 7 million words and 350K sentences.
~2000 sentences were annotated by crowd members (3-10 annotators per sentence) for overall sentiment (polarity) and [eight emotions](https://en.wikipedia.org/wiki/Robert_Plutchik#Plutchik's_wheel_of_emotions): anger, disgust, anticipation , fear, joy, sadness, surprise and trust. 
The percentage of sentences in which each emotion appeared is found in the table below.

|       | anger | disgust | expectation | fear | happy | sadness | surprise | trust | sentiment |
|------:|------:|--------:|------------:|-----:|------:|--------:|---------:|------:|-----------|
| **ratio** |  0.78 |    0.83 |        0.58 | 0.45 |  0.12 |    0.59 |     0.17 |  0.11 | 0.25      |



## Performance
### Emotion Recognition
| emotion     | f1-score | precision | recall   |
|-------------|----------|-----------|----------|
|       anger | 0.96 |  0.99 | 0.93 |
|     disgust | 0.97 |  0.98 | 0.96 |
|anticipation | 0.82 |  0.80 | 0.87 |
|        fear | 0.79 |  0.88 | 0.72 |
|       joy   | 0.90 |  0.97 | 0.84 |
|     sadness | 0.90 |  0.86 | 0.94 |
|    surprise | 0.40 |  0.44 | 0.37 |
|       trust | 0.83 |  0.86 | 0.80 |

*The above metrics is for positive class (meaning, the emotion is reflected in the text).*

### Sentiment (Polarity) Analysis
|              | precision | recall | f1-score |
|--------------|-----------|--------|----------|
| neutral      | 0.83      | 0.56   | 0.67     |
| positive     | 0.96      | 0.92   | 0.94     |
| negative     | 0.97      | 0.99   | 0.98     |
| accuracy     |           |        | 0.97     |
| macro avg    | 0.92      | 0.82   | 0.86     |
| weighted avg | 0.96      | 0.97   | 0.96     |

*Sentiment (polarity) analysis model is also available on AWS! for more information visit [AWS' git](https://github.com/aws-samples/aws-lambda-docker-serverless-inference/tree/main/hebert-sentiment-analysis-inference-docker-lambda)*

## How to use

### Emotion Recognition Model
An online model can be found at [huggingface spaces](https://huggingface.co/spaces/avichr/HebEMO_demo) or as [colab notebook](https://colab.research.google.com/drive/1Jw3gOWjwVMcZslu-ttXoNeD17lms1-ff?usp=sharing)
```
# !pip install pyplutchik==0.0.7
# !pip install transformers==4.14.1

!git clone https://github.com/avichaychriqui/HeBERT.git
from HeBERT.src.HebEMO import *
HebEMO_model = HebEMO()

HebEMO_model.hebemo(input_path = 'data/text_example.txt')
# return analyzed pandas.DataFrame  

hebEMO_df = HebEMO_model.hebemo(text='החיים יפים ומאושרים', plot=True)
```
<img src="https://github.com/avichaychriqui/HeBERT/blob/main/data/hebEMO1.png?raw=true" width="300" height="300" />

  

### For sentiment classification model (polarity ONLY):
	from transformers import AutoTokenizer, AutoModel, pipeline

	tokenizer = AutoTokenizer.from_pretrained("avichr/heBERT_sentiment_analysis") #same as 'avichr/heBERT' tokenizer
	model = AutoModel.from_pretrained("avichr/heBERT_sentiment_analysis")
	
	# how to use?
	sentiment_analysis = pipeline(
	    "sentiment-analysis",
	    model="avichr/heBERT_sentiment_analysis",
	    tokenizer="avichr/heBERT_sentiment_analysis",
	    return_all_scores = True
	)
	
	sentiment_analysis('אני מתלבט מה לאכול לארוחת צהריים')	
	>>>  [[{'label': 'neutral', 'score': 0.9978172183036804},
	>>>  {'label': 'positive', 'score': 0.0014792329166084528},
	>>>  {'label': 'negative', 'score': 0.0007035882445052266}]]

	sentiment_analysis('קפה זה טעים')
	>>>  [[{'label': 'neutral', 'score': 0.00047328314394690096},
	>>>  {'label': 'possitive', 'score': 0.9994067549705505},
	>>>  {'label': 'negetive', 'score': 0.00011996887042187154}]]

	sentiment_analysis('אני לא אוהב את העולם')
	>>>  [[{'label': 'neutral', 'score': 9.214012970915064e-05}, 
	>>>  {'label': 'possitive', 'score': 8.876807987689972e-05}, 
	>>>  {'label': 'negetive', 'score': 0.9998190999031067}]]



## Contact us
[Avichay Chriqui](mailto:avichayc@mail.tau.ac.il) <br>
[Inbal yahav](mailto:inbalyahav@tauex.tau.ac.il) <br>
The Coller Semitic Languages AI Lab <br>
Thank you, תודה, شكرا <br>

## If you used this model please cite us as :
Chriqui, A., & Yahav, I. (2021). HeBERT & HebEMO: a Hebrew BERT Model and a Tool for Polarity Analysis and Emotion Recognition. arXiv preprint arXiv:2102.01909.
```
@article{chriqui2021hebert,
  title={HeBERT \& HebEMO: a Hebrew BERT Model and a Tool for Polarity Analysis and Emotion Recognition},
  author={Chriqui, Avihay and Yahav, Inbal},
  journal={arXiv preprint arXiv:2102.01909},
  year={2021}
}
```


