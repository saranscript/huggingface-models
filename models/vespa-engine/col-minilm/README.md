# MS Marco Ranking with ColBERT on Vespa.ai 

Model is based on [ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT](https://arxiv.org/abs/2004.12832). 
This BERT model is based on [cross-encoder/ms-marco-MiniLM-L-6-v2](https://huggingface.co/cross-encoder/ms-marco-MiniLM-L-6-v2) and trained using the
original [ColBERT training routine](https://github.com/stanford-futuredata/ColBERT/).

This model has 22.3M trainable parameters and is approximately 2x faster than 
[vespa-engine/colbert-medium](https://huggingface.co/vespa-engine/colbert-medium) and with better or on pair MRR@10 on dev. 

The model weights have been tuned by training using a randomized sample of MS Marco training triplets 
[MSMARCO-Passage-Ranking](https://github.com/microsoft/MSMARCO-Passage-Ranking). 

To use this model with vespa.ai for MS Marco Passage Ranking, see 
[MS Marco Ranking using Vespa.ai sample app](https://github.com/vespa-engine/sample-apps/tree/master/msmarco-ranking).

# MS Marco Passage Ranking

| MS Marco Passage Ranking Query Set | MRR@10 ColBERT on Vespa.ai |
|------------------------------------|----------------|
| Dev                                | 0.364          |

Recall@k On Dev (6980 queries)

|K                                   | Recall@K |
|------------------------------------|----------------|
| 50                                 | 0.816          |
| 200                                | 0.905          |
| 1000                               | 0.939          |


The MRR@10 on dev is achieved by re-ranking 1K retrieved by a dense retriever based on 
[sentence-transformers/msmarco-MiniLM-L-6-v3](https://huggingface.co/sentence-transformers/msmarco-MiniLM-L-6-v3). Re-ranking the original top 1000 dev 
is 0.354 MRR@10 (Recall@1K 0.82).

The official baseline BM25 ranking model MRR@10 0.16 on eval and 0.167 on dev question set. 
See [MS Marco Passage Ranking Leaderboard](https://microsoft.github.io/msmarco/).

## Export ColBERT query encoder to ONNX 
We represent the ColBERT query encoder in the Vespa runtime, to map the textual query representation to the tensor representation. For this
we use Vespa's support for running ONNX models. One can use the following snippet to export the model for serving.

```python
from transformers import BertModel
from transformers import BertPreTrainedModel
from transformers import BertConfig
import torch 
import torch.nn as nn

class VespaColBERT(BertPreTrainedModel):
   
    def __init__(self,config):
        super().__init__(config)
        self.bert = BertModel(config)
        self.linear = nn.Linear(config.hidden_size, 32, bias=False)
        self.init_weights()
        
    def forward(self, input_ids, attention_mask):
        Q = self.bert(input_ids,attention_mask=attention_mask)[0]
        Q = self.linear(Q)
        return torch.nn.functional.normalize(Q, p=2, dim=2)  

colbert_query_encoder = VespaColBERT.from_pretrained("vespa-engine/col-minilm") 

#Export model to ONNX for serving in Vespa 

input_names = ["input_ids", "attention_mask"]
output_names = ["contextual"]
#input, max 32 query term
input_ids = torch.ones(1,32, dtype=torch.int64)
attention_mask = torch.ones(1,32,dtype=torch.int64)
args = (input_ids, attention_mask)
torch.onnx.export(colbert_query_encoder,
                args=args,
                f="query_encoder_colbert.onnx",
                input_names = input_names,
                output_names = output_names,
                dynamic_axes = {
                    "input_ids": {0: "batch"},
                    "attention_mask": {0: "batch"},
                    "contextual": {0: "batch"},
                },
                opset_version=11)
```

# Representing the model on Vespa.ai
See [Ranking with ONNX models](https://docs.vespa.ai/documentation/onnx.html) and [MS Marco Ranking sample app](https://github.com/vespa-engine/sample-apps/tree/master/msmarco-ranking)

