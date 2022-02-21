## YAML metadata section

```
---
language:
- el
tags:
- Punctuation Prediction
license: apache-2.0
inference: false
---
```




This model is a finetuning of bert-base-greek-uncased as a Token Classifier which predicts at each token which punctuation mark it is followed by. The model preprocesses everything to lowercase and removes all Greek diacritics. For information on pretraining of the Greek Bert model, please refer to [Greek Bert](https://huggingface.co/nlpaueb/bert-base-greek-uncased-v1)

# Finetuning Parameters

Epochs: 5  
Maximum Sequence Length: 512  
Learning Rate: 4e−5  
Batch Size: 16  

Finetuning Data:  
Greek Europarl data available at: https://opus.nlpl.eu/Europarl.php

Tokens: 44.1M  
Sentences: 1.6M  

Punctuation Points Recognised:  
'.' (0) : Full stop  
',' (1) : Comma  
';' (2) : Greek question mark  
'-' (3) : Dash  
':' (4) : Semicolon  
'0' (5) : No punctuation point is following


# Load Finetuned Model
~~~
from transformers import AutoTokenizer, AutoModelForTokenClassification
tokenizer = AutoTokenizer.from_pretrained("Andrianos/bert-base-greek-punctuation-prediction-finetuned")
model = AutoModelForTokenClassification.from_pretrained("Andrianos/bert-base-greek-punctuation-prediction-finetuned")
~~~

# Using the Model

If you are interested in trying out examples and finding the limitations of the model, the starter Python code to use the model is available at [Github Repo](https://github.com/Andrian0s/Greek-Transformer-Model-Punctuation-Prediction)

# Examples of the Model
Using the demo script, we tried out a few brief examples and show the results below

Input | Input with Predictions
------------- | -------------
"προσεκτικά στον δρομο θα σε περιμενω"  | "προσεκτικα στον δρομο, θα σε περιμενω"
"τι θα φας για βραδινο"  | "τι θα φας για βραδινο;"
"κυριε μαυροκέφαλε εσπασε η κεραια του διαδικτυου θα παρω τηλεφωνο την cyta"  |  "κυριε μαυροκεφαλε, εσπασε η κεραια του διαδικτυου. θα παρω τηλεφωνο την cyta."
"κυριε μαυροκεφαλε εσπασεν η αντεννα του ιντερνετ εννα πιαω τηλεφωνον την cyta"   | "κυριε μαυροκεφαλε, εσπασεν η αντεννα του ιντερνετ. εννα πιαω τηλεφωνον την cyta."

The last two examples have identical meanings, the first is written in plain Modern Greek and the latter in the Cypriot Dialect. It is interesting to see the model performs similarly, even if some words and suffixes are out of vocabulary.

# Further Performance Improvements

We would be happy to hear people have finetuned this model with more and diverse datasets, as we expect this to increase robustness.
Within our research, improvements to consistency in punctuation prediction have shown to be possible with techniques such as sliding windows (during inference) for larger documents, weighted loss and ensembling of different models. Make sure to cite our work when you further our models with the aforementioned techniques.

# Author
This model is further work based on the winning submission at Shared Task 2 Sentence End and Punctuation Prediction in NLG Text at SwissText2021.  
The winning submission is entitled "UZH OnPoint at Swisstext-2021: Sentence End and Punctuation Prediction in NLG Text Through Ensembling of Different Transformers" in the Proceedings of the 6th SwissText Held Online. It is publicly available at http://ceur-ws.org/Vol-2957/sepp_paper2.pdf

If you use the model, please cite the following:

@inproceedings{ST2021-OnPoint,
 title={UZH OnPoint at Swisstext-2021: Sentence End and Punctuation Prediction in NLG Text Through Ensembling of Different Transformers},
 author={Michail, Andrianos and Wehrli, Silvan and Bucková, Terézia},
 booktitle={Proceedings of the 1st Shared Task on Sentence
 End and Punctuation Prediction in NLG Text (SEPPNLG 2021) at SwissText 2021},
 year={2021}
}

Model Finetuned and released by Andrianos Michail with resources provided by [Department of Computational Linguistics, University of Zurich](https://www.cl.uzh.ch/en.html)

| Github: [@Andrian0s](https://github.com/Andrian0s) | LinkedIn: [amichail2](https://www.linkedin.com/in/amichail2/)