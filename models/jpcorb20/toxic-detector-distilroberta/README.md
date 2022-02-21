# Distilroberta for toxic comment detection

See my GitHub repo [toxic-comment-server](https://github.com/jpcorb20/toxic-comment-server)

The model was trained from [DistilRoberta](https://huggingface.co/distilroberta-base) on [Kaggle Toxic Comments](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge) with the BCEWithLogits loss for Multi-Label prediction. Thus, please use the sigmoid activation on the logits (not made to use the softmax output, e.g. like the HF widget).

## Evaluation

  F1 scores:
  
      toxic: 0.72
      severe_toxic: 0.38
      obscene: 0.72
      threat: 0.52
      insult: 0.69
      identity_hate: 0.60
  
      Macro-F1: 0.61