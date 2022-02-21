-修改为相对位置
-对内容类型进行修改

```python

from transformers import BertTokenizer, BertModel,BertConfig


Config = BertConfig.from_pretrained("napoler/chinese_roberta_L-2_H-512_relative_key_query_token_type_100")
tokenizer = BertTokenizer.from_pretrained('napoler/chinese_roberta_L-2_H-512_relative_key_query_token_type_100')
model = BertModel.from_pretrained("napoler/chinese_roberta_L-2_H-512_relative_key_query_token_type_100",config=Config)


```

修改方案

https://www.kaggle.com/terrychanorg/bert-notebook9525623d9e