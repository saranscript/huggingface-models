- You'll need to instantiate a special RoBERTa class. Though technically a "Longformer", the elongated RoBERTa model will still need to be pulled in as such.
- To do so, use the following classes:

```python
class RobertaLongSelfAttention(LongformerSelfAttention):
    def forward(
        self,
        hidden_states,
        attention_mask=None,
        head_mask=None,
        encoder_hidden_states=None,
        encoder_attention_mask=None,
        output_attentions=False,
    ):
        return super().forward(hidden_states, attention_mask=attention_mask, output_attentions=output_attentions)

class RobertaLongForMaskedLM(RobertaForMaskedLM):
    def __init__(self, config):
        super().__init__(config)
        for i, layer in enumerate(self.roberta.encoder.layer):
            # replace the `modeling_bert.BertSelfAttention` object with `LongformerSelfAttention`
            layer.attention.self = RobertaLongSelfAttention(config, layer_id=i)
```
- Then, pull the model as ```RobertaLongForMaskedLM.from_pretrained('simonlevine/bioclinical-roberta-long')```
- Now, it can be used as usual. Note you may get untrained weights warnings.
- Note that you can replace ```RobertaForMaskedLM``` with a different task-specific RoBERTa from Huggingface, such as RobertaForSequenceClassification.
