fintuned the kykim/bert-kor-base model as a dense passage retrieval context encoder by KLUE dataset
this link is experiment result. https://wandb.ai/thingsu/DenseRetrieval

Corpus : Korean Wikipedia Corpus 

Trained Strategy : 
 - Pretrained Model : kykim/bert-kor-base 
 - Inverse Cloze Task : 16 Epoch, by korquad v 1.0, KLUE MRC dataset
 - In-batch Negatives : 12 Epoch, by KLUE MRC dataset, random sampling between Sparse Retrieval(TF-IDF) top 100 passage per each query
 
You must need to use Korean wikipedia corpus

<pre>
<code>
from Transformers import AutoTokenizer, BertPreTrainedModel, BertModel

class BertEncoder(BertPreTrainedModel):
    def __init__(self, config):
        super(BertEncoder, self).__init__(config)
        
        self.bert = BertModel(config)
        self.init_weights()


    def forward(self, input_ids, attention_mask=None, token_type_ids=None):
        outputs = self.bert(input_ids, attention_mask, token_type_ids)
        pooled_output = outputs[1]
        return pooled_output
        
model_name = 'kykim/bert-kor-base' 
tokenizer = AutoTokenizer.from_pretrained(model_name)

q_encoder = BertEncoder.from_pretrained("thingsu/koDPR_question")
p_encoder = BertEncoder.from_pretrained("thingsu/koDPR_context")

</code>
</pre>