pip install vaderSentiment

from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
analyser = SentimentIntensityAnalyzer()

analyser.polarity_scores("I hate watching movies")  

import nltk
from nltk.tokenize import word_tokenize, RegexpTokenizer
from nltk.sentiment.vader import SentimentIntensityAnalyzer

nltk.download('all')

import numpy as np

sentence = """I love dancing & painting"""
tokenized_sentence = nltk.word_tokenize(sentence)

from nltk import word_tokenize
from typing import List

Analyzer = SentimentIntensityAnalyzer()

pos_word_list=[]
neu_word_list=[]
neg_word_list=[]
pos_score_list=[]
neg_score_list=[]
score_list=[]
for word in tokenized_sentence:
    if (Analyzer.polarity_scores(word)['compound']) >= 0.1:
        pos_word_list.append(word)
        score_list.append(Analyzer.polarity_scores(word)['compound'])
    elif (Analyzer.polarity_scores(word)['compound']) <= -0.1:
        neg_word_list.append(word)
        score_list.append(Analyzer.polarity_scores(word)['compound'])
    else:
        neu_word_list.append(word)
        score_list.append(Analyzer.polarity_scores(word)['compound'])

print('Positive:',pos_word_list)
print('Neutral:',neu_word_list)
print('Negative:',neg_word_list) 
print('Score:', score_list)
score = Analyzer.polarity_scores(sentence)
print('\nScores:', score)

predict_log=score.values()
value_iterator=iter(predict_log)
neg_prediction=next(value_iterator)
neu_prediction=next(value_iterator)
pos_prediction=next(value_iterator)

prediction_list=[neg_prediction, pos_prediction]
prediction_list_array=np.array(prediction_list)


def predict():
        probs = []
        for text in texts:
            offset = (self.score(text) + 1) / 2.
            binned = np.digitize(5 * offset, self.classes) + 1
            simulated_probs = scipy.stats.norm.pdf(self.classes, binned, scale=0.5)
            probs.append(simulated_probs)
        return np.array(probs)

latex_special_token = ["!@#$%^&*()"]

import operator

def generate(text_list, attention_list, latex_file, color_neg='red', color_pos='green', rescale_value = False):
  print("hello")
  attention_list = rescale(attention_list)
  word_num = len(text_list)
  print(len(attention_list))
  print(len(text_list))
 
    
  text_list = clean_word(text_list)
  with open(latex_file,'w') as f:
    f.write(r'''\documentclass[varwidth]{standalone}
\special{papersize=210mm,297mm}
\usepackage{color}
\usepackage{tcolorbox}
\usepackage{CJK}
\usepackage{adjustbox}
\tcbset{width=0.9\textwidth,boxrule=0pt,colback=red,arc=0pt,auto outer arc,left=0pt,right=0pt,boxsep=5pt}
\begin{document}
\begin{CJK*}{UTF8}{gbsn}'''+'\n')
    string = r'''{\setlength{\fboxsep}{0pt}\colorbox{white!0}{\parbox{0.9\textwidth}{'''+"\n"
    for idx in range(len(attention_list)):
      if attention_list[idx] > 0:
        string += "\\colorbox{%s!%s}{"%(color_pos, attention_list[idx])+"\\strut " + text_list[idx]+"} "
      else:
        string += "\\colorbox{%s!%s}{"%(color_neg, -attention_list[idx])+"\\strut " + text_list[idx]+"} "
          
    string += "\n}}}"
    f.write(string+'\n')
    f.write(r'''\end{CJK*}
\end{document}''')

  

def rescale(input_list):
  
  the_array = np.asarray(input_list)
  the_max = np.max(abs(the_array))
  rescale = the_array/the_max
  rescale = rescale*100
  rescale = np.round(rescale, 3)
  
  '''
  the_array = np.asarray(input_list)
  the_max = np.max(the_array)
  the_min = np.min(the_array)
  rescale = ((the_array - the_min)/(the_max-the_min))*100
  for i in rescale:
    print(rescale)
  '''
  
  return rescale.tolist()

def clean_word(word_list):
	new_word_list = []
	for word in word_list:  
		for latex_sensitive in ["\\", "%", "&", "^", "#", "_",  "{", "}"]:
			if latex_sensitive in word:
				word = word.replace(latex_sensitive, '\\'+latex_sensitive)
		new_word_list.append(word)
	return new_word_list

if __name__ == '__main__':
  color_1 = 'red'
  color_2 = 'green'
  words = word_tokenize(sentence)
  word_num = len(words)
  generate(words, score_list, "sple.tex", color_1, color_2)


