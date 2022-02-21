# About this model: Topical Change Detection in Documents
This network has been fine-tuned for the task described in the paper *Topical Change Detection in Documents via Embeddings of Long Sequences* and is our best-performing base-transformer model. You can find more detailed information in our GitHub page for the paper [here](https://github.com/dennlinger/TopicalChange), or read the [paper itself](https://arxiv.org/abs/2012.03619). The weights are based on RoBERTa-base.

# Load the model
```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer
tokenizer = AutoTokenizer.from_pretrained('dennlinger/roberta-cls-consec')
model = AutoModelForSequenceClassification.from_pretrained('dennlinger/roberta-cls-consec')
```

# Input Format
The model expects two segments that are separated with the `[SEP]` token. In our training setup, we had entire paragraphs as samples (or up to 512 tokens across two paragraphs), specifically trained on a Terms of Service data set. Note that this might lead to poor performance on "general" topics, such as news articles or Wikipedia.

# Training objective
The training task is to determine whether two text segments (paragraphs) belong to the same topical section or not. This can be utilized to create a topical segmentation of a document by consecutively predicting the "coherence" of two segments.  
If you are experimenting via the Huggingface Model API, the following are interpretations of the `LABEL`s:
* `LABEL_0`: Two input segments separated by `[SEP]` do *not* belong to the same topic.
* `LABEL_1`: Two input segments separated by `[SEP]` do belong to the same topic.

# Performance
The results of this model can be found in the paper. We average over models from five different random seeds, which is why the specific results for this model might be different from the exact values in the paper.

Note that this model is *not* trained to work on classifying single texts, but only works with two (separated) inputs.