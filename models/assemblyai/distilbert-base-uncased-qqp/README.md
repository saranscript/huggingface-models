# DistilBERT-Base-Uncased for Duplicate Question Detection
This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) originally released in ["DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter"](https://arxiv.org/abs/1910.01108) and trained on the [Quora Question Pairs](https://quoradata.quora.com/First-Quora-Dataset-Release-Question-Pairs) dataset; part of the [General Language Understanding Evaluation (GLUE)](https://gluebenchmark.com) benchmark. This model was fine-tuned by the team at [AssemblyAI](https://www.assemblyai.com) and is released with the [corresponding blog post]().  

## Usage
To download and utilize this model for duplicate question detection please execute the following:
```python
import torch.nn.functional as F 
from transformers import AutoTokenizer, AutoModelForSequenceClassification
tokenizer = AutoTokenizer.from_pretrained("assemblyai/distilbert-base-uncased-qqp")
model = AutoModelForSequenceClassification.from_pretrained("assemblyai/distilbert-base-uncased-qqp")

tokenized_segments = tokenizer(["How many hours does it take to fly from California to New York?"], ["What is the flight time from New York to Seattle?"], return_tensors="pt", padding=True, truncation=True)
tokenized_segments_input_ids, tokenized_segments_attention_mask = tokenized_segments.input_ids, tokenized_segments.attention_mask
model_predictions = F.softmax(model(input_ids=tokenized_segments_input_ids, attention_mask=tokenized_segments_attention_mask)['logits'], dim=1)

print("Duplicate probability: "+str(model_predictions[0][1].item()*100)+"%")
print("Non-duplicate probability: "+str(model_predictions[0][0].item()*100)+"%")
```

For questions about how to use this model feel free to contact the team at [AssemblyAI](https://www.assemblyai.com)!