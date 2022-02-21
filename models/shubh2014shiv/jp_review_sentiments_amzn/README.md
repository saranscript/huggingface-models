# Steps to use this model
This model uses tokenizer 'rinna/japanese-roberta-base'. Therefore, below steps are critical to run the model correctly.

1. Create a local root directory on your system and new python environment.
2. Install below requirements 

```
transformers==4.12.2
torch==1.10.0
numpy==1.21.3
pandas==1.3.4
sentencepiece==0.1.96
```
3. Go to link: "https://huggingface.co/spaces/shubh2014shiv/Japanese_NLP/tree/main" and download the fine tuned weights "reviewSentiments_jp.pt" in same local root directory.
4. Rename the downloaded weights as "reviewSentiments_jp.pt"
5. Use below code in the newly created environment.

```
from transformers import T5Tokenizer,BertForSequenceClassification
import torch
tokenizer = T5Tokenizer.from_pretrained('rinna/japanese-roberta-base')
japanese_review_text = "履きやすい。タイムセールで購入しました。見た目以上にカッコいいです。(^^)"
encoded_data = tokenizer.batch_encode_plus([japanese_review_text ],
                                                   add_special_tokens=True,
                                                   return_attention_mask=True,
                                                   padding=True,
                                                   max_length=200,
                                                   return_tensors='pt',
                                                   truncation=True)
input_ids = encoded_data['input_ids']
attention_masks = encoded_data['attention_mask']
model = BertForSequenceClassification.from_pretrained("shubh2014shiv/jp_review_sentiments_amzn",
                                                                      num_labels=2,
                                                                      output_attentions=False,
                                                                      output_hidden_states=False)
model.load_state_dict(torch.load('reviewSentiments_jp.pt',map_location=torch.device('cpu')))
inputs = { 'input_ids': input_ids,
              'attention_mask': attention_masks}
with torch.no_grad():
  outputs = model(**inputs)

logits = outputs.logits
logits = logits.detach().cpu().numpy()
scores = 1 / (1 + np.exp(-1 * logits))
result = {"TEXT (文章)": jp_review_text,'NEGATIVE (ネガティブ)': scores[0][0], 'POSITIVE (ポジティブ)': scores[0][1]}
```

Output:

{'TEXT (文章)': '履きやすい。タイムセールで購入しました。見た目以上にカッコいいです。(^^)', 'NEGATIVE (ネガティブ)': 0.023672901, 'POSITIVE (ポジティブ)': 0.96819043}