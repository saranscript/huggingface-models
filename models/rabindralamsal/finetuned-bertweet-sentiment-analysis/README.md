# Sentiment Analysis of English Tweets with BERTsent

**BERTsent**: A finetuned **BERT** based **sent**iment classifier for English language tweets.

BERTsent is trained with SemEval 2017 corpus (39k plus tweets) and is based on [bertweet-base](https://github.com/VinAIResearch/BERTweet) that was trained on 850M English Tweets (cased) and additional 23M COVID-19 English Tweets (cased). The base model used [RoBERTa](https://github.com/pytorch/fairseq/blob/master/examples/roberta/README.md) pre-training procedure.

Output labels:

 - 0 represents "negative" sentiment
 - 1 represents "neutral" sentiment
 - 2 represents "positive" sentiment

## Using the model

Install transformers and emoji, if already not installed:

    terminal:
            pip install transformers
            pip install emoji (for converting emoticons or emojis into text)
    notebooks (Colab, Kaggle):
            !pip install transformers
            !pip install emoji

Import BERTsent from the transformers library:

    from transformers import AutoTokenizer, TFAutoModelForSequenceClassification
      
    tokenizer = AutoTokenizer.from_pretrained("rabindralamsal/finetuned-bertweet-sentiment-analysis")
    
    model = TFAutoModelForSequenceClassification.from_pretrained("rabindralamsal/finetuned-bertweet-sentiment-analysis")

Import TensorFlow and numpy:

    import tensorflow as tf
    import numpy as np

We have installed and imported everything that's needed for the sentiment analysis. Let's predict sentiment of an example tweet:

    example_tweet = "The NEET exams show our Govt in a poor light: unresponsiveness to genuine concerns; admit cards not delivered to aspirants in time; failure to provide centres in towns they reside, thus requiring unnecessary & risky travels. What a disgrace to treat our #Covid warriors like this!"
    #this tweet resides on Twitter with an identifier-1435793872588738560
        
    input = tokenizer.encode(example_tweet, return_tensors="tf")
    output = model.predict(input)[0]
    prediction = tf.nn.softmax(output, axis=1).numpy()
    sentiment = np.argmax(prediction)
        
    print(prediction)
    print(sentiment)

Output: 

    [[0.972672164440155  0.023684727028012276 0.003643065458163619]]
    0